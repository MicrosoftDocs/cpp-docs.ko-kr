---
title: 혼합형 어셈블리 초기화
description: 혼합 어셈블리를 로드 하 고 초기화 하는 동안 발생할 수 있는 문제를 처리 합니다.
ms.date: 09/26/2020
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
ms.openlocfilehash: 6767e6087999138f8e62d3c5a58f972b4e2149ed
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413816"
---
# <a name="initialization-of-mixed-assemblies"></a>혼합형 어셈블리 초기화

Windows 개발자는에서 코드를 실행할 때 항상 로더 잠금을 주의 해야 합니다 `DllMain` . 그러나 c + +/CLI 혼합 모드 어셈블리를 처리할 때 고려해 야 할 몇 가지 추가 문제가 있습니다.

[DllMain](/windows/win32/Dlls/dllmain) 내의 코드는 .net CLR (공용 언어 런타임)에 액세스 해서는 안 됩니다. 즉 `DllMain` ,에서 직접 또는 간접적으로 관리 되는 함수를 호출 하지 않아야 합니다 .에서는 관리 코드를 선언 하거나 구현 하지 않아야 `DllMain` 하며, 내에서 가비지 컬렉션 또는 자동 라이브러리 로드를 수행 하지 않아야 `DllMain` 합니다.

## <a name="causes-of-loader-lock"></a>로더 잠금 원인

.NET 플랫폼의 도입에는 실행 모듈 (EXE 또는 DLL)을 로드 하는 두 가지 메커니즘이 있습니다. 하나는 관리 되지 않는 모듈에 사용 되 고, 다른 하나는 .NET 어셈블리를 로드 하는 CLR에 사용 됩니다. 혼합 DLL 로드 문제는 Microsoft Windows OS 로더에 주로 관련된 것입니다.

.NET 구문만 포함 된 어셈블리를 프로세스에 로드 하는 경우 CLR 로더에서는 필요한 모든 로드 및 초기화 작업을 수행할 수 있습니다. 그러나 네이티브 코드 및 데이터를 포함할 수 있는 혼합 어셈블리를 로드 하려면 Windows 로더도 사용 해야 합니다.

Windows 로더는 초기화 되기 전에 해당 DLL의 코드나 데이터에 액세스할 수 없도록 보장 합니다. 그리고 부분적으로 초기화 되는 동안 코드에서 DLL을 중복 해 서 로드할 수 없도록 합니다. 이렇게 하기 위해 Windows 로더에서는 모듈을 초기화 하는 동안 안전 하지 않은 액세스를 방지 하는 프로세스 전역 임계 영역 ("로더 잠금"이 라고도 함)을 사용 합니다. 따라서 로드 프로세스는 기존의 여러 교착 시나리오에 취약합니다. 혼합형 어셈블리의 경우 다음과 같은 두 가지 시나리오에서 특히 교착 상태의 위험이 증가합니다.

- 첫째, 사용자가 로더 잠금이 유지 될 때 MSIL (Microsoft 중간 언어)로 컴파일된 함수를 실행 하려고 하면 ( `DllMain` 예:) 교착 상태가 발생할 수 있습니다. MSIL 함수가 아직 로드 되지 않은 어셈블리의 형식을 참조 하는 경우를 고려 합니다. CLR은 이 어셈블리를 자동으로 로드하려고 하며, 이를 위해서는 Windows 로더에서 로드 잠금을 걸어야 합니다. 로더 잠금은 호출 시퀀스의 이전 코드에서 이미 보유 하 고 있으므로 교착 상태가 발생 합니다. 그러나 로더 잠금 상태에서 MSIL을 실행 하면 교착 상태가 발생 하는 것을 보장할 수 없습니다. 이를 통해이 시나리오를 진단 하 고 수정 하기는 어렵습니다. 참조 되는 형식의 DLL에 네이티브 구문이 없고 모든 종속성에 네이티브 구문이 포함 되어 있지 않은 경우와 같은 일부 상황에서는 Windows 로더에서 참조 되는 형식의 .NET 어셈블리를 로드할 필요가 없습니다. 또한 필수 어셈블리나 해당 혼합 네이티브/.NET 종속 항목이 이미 다른 코드를 통해 로드되었을 수도 있습니다. 따라서 교착 상태는 예측하기가 매우 어려우며 대상 컴퓨터의 구성에 따라 크게 달라질 수 있습니다.

- 둘째, .NET Framework 버전 1.0 및 1.1에서 Dll을 로드 하는 경우 CLR에서는 로더 잠금이 유지 되지 않았다고 가정 하 고 로더 잠금 상태에서 유효 하지 않은 몇 가지 작업을 수행 했습니다. 로더 잠금이 보유 되지 않는다고 가정 하는 것은 순수 .NET Dll에 대 한 올바른 가정입니다. 그러나 혼합 Dll은 네이티브 초기화 루틴을 실행 하므로 네이티브 Windows 로더가 필요 하므로 로더 잠금이 필요 합니다. 따라서 개발자가 DLL 초기화 과정에서 MSIL 함수를 실행 하지 않은 경우에도 1.0 및 1.1 .NET Framework 버전에서 비결 정적 교착 상태가 발생 하는 것은 여전히 발생 합니다.

혼합 DLL 로드 프로세스의 모든 불명확한 요소가 제거되었습니다. 이러한 변경 작업은 다음과 같이 수행 되었습니다.

- CLR이 혼합 DLL을 로드할 때 잘못된 가정을 내리지 않습니다.

- 관리 되지 않는 초기화와 관리 되는 초기화는 서로 다른 두 단계에서 수행 됩니다. 관리 되지 않는 초기화는 먼저 발생 하 `DllMain` 고 관리 되는 초기화는를 통해 나중에 수행 됩니다. NET에서 지원 되는 `.cctor` 구문입니다. 또는를 사용 하지 않는 한 후자는 사용자에 게 완전히 투명 합니다 **`/Zl`** **`/NODEFAULTLIB`** . 자세한 내용은[ `/NODEFAULTLIB` (라이브러리 무시)](../build/reference/nodefaultlib-ignore-libraries.md) 및 [ `/Zl` (기본 라이브러리 이름 생략)](../build/reference/zl-omit-default-library-name.md)를 참조 하세요.

로더 잠금이 여전히 발생할 수 있지만 이제 잠금이 일정하게 발생하며 이를 감지할 수 있습니다. `DllMain`에 MSIL 명령이 포함 되어 있으면 컴파일러에서 [컴파일러 경고 (수준 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)를 생성 합니다. 또한 CRT 또는 CLR에서는 로더 잠금 상황에서 MSIL을 실행하려는 시도를 감지 및 보고합니다. CRT에서 이러한 상황이 감지되면 런타임 진단 C 런타임 오류 R6033이 발생합니다.

이 문서의 나머지 부분에서는 로더 잠금 상태에서 MSIL을 실행할 수 있는 나머지 시나리오에 대해 설명 합니다. 이러한 각 시나리오에서 문제를 해결 하는 방법과 디버깅 기법을 보여 줍니다.

## <a name="scenarios-and-workarounds"></a>시나리오 및 해결 방법

로더 잠금 상태에서 사용자 코드가 MSIL을 실행할 수 있는 상황에는 여러 가지가 있습니다. 개발자는 이러한 상황에서 사용자 코드 구현이 MSIL 명령을 실행 하지 않도록 해야 합니다. 다음 각 하위 섹션에서는 가능한 모든 상황과 가장 일반적인 경우에 발생하는 문제를 해결하는 방법에 대해 설명합니다.

### <a name="dllmain"></a>DllMain

`DllMain`함수는 DLL에 대 한 사용자 정의 진입점입니다. 사용자가 별도로 지정하지 않으면 프로세스나 스레드를 포함 DLL에 연결하거나 해당 DLL에서 분리할 때마다 `DllMain` 이 호출됩니다. 이러한 호출은 로더 잠금 상태에서 발생할 수 있으므로 사용자가 제공한 `DllMain` 함수를 MSI로 컴파일하지 않아야 합니다. 또한 루트가 `DllMain` 에 있는 호출 트리의 어떠한 함수도 MSIL로 컴파일할 수 없습니다. 여기에서 문제를 해결 하려면을 정의 하는 코드 블록을 `DllMain` 로 수정 해야 합니다 `#pragma unmanaged` . `DllMain` 을 호출하는 모든 함수에 대해 동일한 작업을 수행해야 합니다.

이러한 함수가 다른 호출 컨텍스트에 대해 MSIL 구현이 필요한 함수를 호출 해야 하는 경우에는 동일한 함수의 .NET 및 네이티브 버전이 모두 만들어지는 중복 전략을 사용할 수 있습니다.

`DllMain`또는 로더 잠금 상태에서 실행할 필요가 없는 경우에는 사용자가 제공한 구현을 제거 하 여 문제를 방지할 수 있습니다 `DllMain` .

에서 `DllMain` MSIL을 직접 실행 하려고 하면 [컴파일러 경고 (수준 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) 이 발생 합니다. 그러나에서 `DllMain` MSIL을 실행 하려는 다른 모듈의 함수를 호출 하는 경우에는 컴파일러에서 검색할 수 없습니다.

이 시나리오에 대 한 자세한 내용은 [진단 장애 요소](#impediments-to-diagnosis)를 참조 하세요.

### <a name="initializing-static-objects"></a>정적 개체 초기화

동적 이니셜라이저가 필요한 경우 정적 개체를 초기화하면 교착 상태가 발생할 수 있습니다. 컴파일 타임에 알려진 값을 정적 변수에 할당 하는 경우와 같이 간단한 경우에는 동적 초기화가 필요 하지 않으므로 교착 상태의 위험이 없습니다. 그러나 일부 정적 변수는 컴파일 타임에 계산 될 수 없는 식, 생성자 호출 또는 함수에 의해 초기화 됩니다. 이러한 변수에는 모듈을 초기화 하는 동안 코드를 실행 해야 합니다.

아래 코드에서는 함수 호출, 개체 생성 및 포인터 초기화 같이 동적 초기화가 필요한 정적 이니셜라이저의 예를 보여 줍니다. 이러한 예제는 정적이 아니지만 전역 범위에 정의를 포함 하는 것으로 간주 됩니다 .이는 결과가 동일 합니다.

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

교착 상태의 위험은 포함 하는 모듈이로 컴파일되는지 여부 **`/clr`** 와 MSIL이 실행 되는지 여부에 따라 달라 집니다. 특히 정적 변수가 (또는 블록에 있음)를 사용 하지 않고 컴파일된 경우이를 **`/clr`** `#pragma unmanaged` 초기화 하는 데 필요한 동적 이니셜라이저에서 MSIL 명령을 실행 합니다. 교착 상태가 발생할 수 있습니다. 이는를 사용 하지 않고 컴파일된 모듈의 경우 **`/clr`** DllMain에서 정적 변수를 초기화 하기 때문입니다. 반면,로 컴파일된 정적 변수는 **`/clr`** `.cctor` 관리 되지 않는 초기화 단계가 완료 되 고 로더 잠금이 해제 된 후에에 의해 초기화 됩니다.

정적 변수의 동적 초기화로 인해 발생 하는 여러 가지 교착 상태 솔루션이 있습니다. 이러한 작업은 문제를 해결 하는 데 필요한 시간에 따라 대략적으로 정렬 됩니다.

- 정적 변수를 포함 하는 소스 파일은를 사용 하 여 컴파일할 수 있습니다 **`/clr`** .

- 정적 변수를 통해 호출 되는 모든 함수는 지시문을 사용 하 여 네이티브 코드로 컴파일할 수 있습니다 `#pragma unmanaged` .

- 정적 변수가 의존하는 코드를 수동으로 복제하여 .NET 버전과 네이티브 버전에 서로 다른 이름을 지정합니다. 그런 다음 개발자는 네이티브 정적 이니셜라이저에서 네이티브 버전을 호출하고 .NET 버전은 다른 위치에서 호출할 수 있습니다.

### <a name="user-supplied-functions-affecting-startup"></a>시작에 영향을 주는 사용자 제공 함수

시작 시 초기화를 위하여 라이브러리가 의존하는 사용자 제공 함수에는 여러 가지 있습니다. 예를 들어, 및 연산자와 같은 c + +의 전역 오버 로드 연산자의 경우 **`new`** **`delete`** 사용자 제공 버전은 c + + 표준 라이브러리 초기화 및 소멸을 비롯 한 모든 위치에서 사용 됩니다. 따라서 c + + 표준 라이브러리 및 사용자 제공 정적 이니셜라이저는 이러한 연산자의 사용자 제공 버전을 호출 합니다.

사용자 제공 버전을 MSIL로 컴파일하는 경우 이러한 이니셜라이저는 로더 잠금 상태에서도 MSIL 명령을 실행하려 합니다. 사용자가 제공한 경우에 `malloc` 도 동일한 결과가 발생 합니다. 이 문제를 해결 하려면 이러한 오버 로드 또는 사용자 제공 정의를 지시문을 사용 하 여 네이티브 코드로 구현 해야 합니다 `#pragma unmanaged` .

이 시나리오에 대 한 자세한 내용은 [진단 장애 요소](#impediments-to-diagnosis)를 참조 하세요.

### <a name="custom-locales"></a>사용자 지정 로캘

사용자가 사용자 지정 전역 로캘을 제공 하는 경우이 로캘은 정적으로 초기화 된 스트림을 비롯 하 여 이후의 모든 i/o 스트림을 초기화 하는 데 사용 됩니다. 이 전역 로캘 개체를 MSIL로 컴파일하는 경우 MSIL로 컴파일된 로캘 개체 멤버 함수가 로더 잠금 상태에서 호출될 수 있습니다.

이 문제를 해결하는 데는 세 가지 방법이 있습니다.

모든 전역 i/o 스트림 정의를 포함 하는 소스 파일은 옵션을 사용 하 여 컴파일할 수 있습니다 **`/clr`** . 이렇게 하면 해당 정적 이니셜라이저가 로더 잠금 상태에서 실행 되지 않습니다.

지시문을 사용 하 여 사용자 지정 로캘 함수 정의를 네이티브 코드로 컴파일할 수 있습니다 `#pragma unmanaged` .

사용자 지정 로캘을 전역 로캘로 설정하는 것을 로더 잠금이 해제될 때까지 뒤로 미룹니다. 그런 다음 사용자 지정 로캘을 사용하여 초기화할 때 작성된 I/O 스트림을 명시적으로 구성합니다.

## <a name="impediments-to-diagnosis"></a>진단 장애 요소

경우에 따라 교착 상태의 원인을 검색 하기가 어렵습니다. 다음 하위 섹션에서는 이와 관련된 시나리오 및 이러한 문제를 해결하는 방법에 대해 설명합니다.

### <a name="implementation-in-headers"></a>헤더의 구현

특수한 몇 가지 경우 헤더 파일 내의 함수 구현으로 인해 진단이 어려워질 수 있습니다. 인라인 함수와 템플릿 코드는 모두 헤더 파일에 해당 함수를 지정해야 합니다.  C++ 언어는 이름이 동일한 모든 함수 구현을 의미론적으로 동일하게 파악하는 단일 정의 규칙을 사용합니다. 따라서 C++ 링커에서는 특정 함수의 구현이 중복된 개체 파일을 병합할 때 별다른 사항을 고려할 필요가 없습니다.

Visual Studio 2005 이전의 Visual Studio 버전에서 링커는 이러한 의미 체계의 가장 큰 정의 중 가장 큰 정의를 선택 하기만 합니다. 다른 최적화 옵션이 다른 소스 파일에 사용 되는 경우 전방 선언 및 시나리오를 수용 하기 위해 수행 됩니다. 혼합 된 네이티브 및 .NET Dll에 대 한 문제를 만듭니다.

동일한 헤더가 사용 및 사용 안 함으로 설정 된 c + + 파일에 모두 포함 될 수도 있고 **`/clr`** #include 블록 내에 래핑될 수 있으므로 `#pragma unmanaged` 헤더에서 구현을 제공 하는 함수의 MSIL 버전과 네이티브 버전이 모두 있을 수 있습니다. MSIL 및 네이티브 구현에는 로더 잠금에서 초기화에 대 한 의미 체계가 다르며,이는 하나의 정의 규칙을 효과적으로 위반 합니다. 따라서 링커가 가장 큰 구현을 선택할 때 지시문을 사용 하 여 다른 곳에서 네이티브 코드로 명시적으로 컴파일된 경우에도 MSIL 버전의 함수를 선택할 수 있습니다 `#pragma unmanaged` . 로더 잠금 상태에서 MSIL 버전의 템플릿이나 인라인 함수가 호출 되지 않게 하려면 로더 잠금 상태에서 호출 되는 이러한 모든 함수의 정의를 모두 지시문으로 수정 해야 합니다 `#pragma unmanaged` . 세 번째 파티에서 헤더 파일을 사용 하는 경우 이러한 변경 작업을 수행 하는 가장 쉬운 방법은 위반 하는 `#pragma unmanaged` 헤더 파일에 대 한 #include 지시문 주위에 지시문을 푸시하는 것입니다. 예제는 [관리 되는, 관리 되지 않는](../preprocessor/managed-unmanaged.md) 항목을 참조 하세요. 그러나이 전략은 .NET Api를 직접 호출 해야 하는 다른 코드를 포함 하는 헤더에는 적용 되지 않습니다.

로더 잠금 문제를 해결하려는 사용자의 편의를 위해 네이티브 구현과 관리되는 구현이 둘 다 있으면 링커에서 네이티브 구현을 선택합니다. 이 기본값은 위의 문제를 방지 합니다. 그러나이 릴리스에는 컴파일러의 해결 되지 않은 두 가지 문제로 인해이 규칙에 대 한 두 가지 예외가 있습니다.

- 인라인 함수에 대 한 호출은 전역 정적 함수 포인터를 통해 호출 됩니다. 이 시나리오는 가상 함수가 전역 함수 포인터를 통해 호출 되기 때문에 isn'table. 예를 들면 다음과 같습니다.

```cpp
#include "definesmyObject.h"
#include "definesclassC.h"

typedef void (*function_pointer_t)();

function_pointer_t myObject_p = &myObject;

#pragma unmanaged
void DuringLoaderlock(C & c)
{
    // Either of these calls could resolve to a managed implementation,
    // at link-time, even if a native implementation also exists.
    c.VirtualMember();
    myObject_p();
}
```

### <a name="diagnosing-in-debug-mode"></a>디버그 모드에서 진단

로드 잠금 문제에 대한 진단은 모두 디버그 빌드에서 수행해야 합니다. 릴리스 빌드에서 진단을 생성 하지 못할 수 있습니다. 그리고 릴리스 모드에서의 최적화는 로더 잠금 시나리오에서 일부 MSIL을 마스킹할 수 있습니다.

## <a name="how-to-debug-loader-lock-issues"></a>로더 잠금 문제를 디버깅 하는 방법

MSIL 함수를 호출할 때 CLR에서 진단이 생성되면 CLR 실행이 일시 중단됩니다. 그러면 디버기 in-process를 실행 하는 경우에도 Visual C++ 혼합 모드 디버거가 일시 중단 됩니다. 그러나 프로세스에 연결할 때 혼합 디버거를 사용 하 여 디버기의 관리 되는 호출 스택을 가져올 수 없습니다.

로더 잠금 상황에서 호출된 특정 MSIL 함수를 식별하려면 다음 단계를 수행해야 합니다.

1. mscoree.dll 및 mscorwks.dll에 대한 기호를 사용할 수 있는지 확인합니다.

   두 가지 방법으로 기호를 사용할 수 있도록 설정할 수 있습니다. 첫 번째 방법으로 mscoree.dll 및 mscorwks.dll에 대한 PDB를 기호 검색 경로에 추가할 수 있습니다. 추가 하려면 기호 검색 경로 옵션 대화 상자를 엽니다. **도구** 메뉴에서 **옵션**을 선택 합니다. **옵션** 대화 상자의 왼쪽 창에서 **디버깅** 노드를 열고 **기호**를 선택 합니다. mscoree.dll 경로를 추가 하 고 mscorwks.dll PDB 파일을 검색 목록에 추가 합니다. 이러한 PDB는 %VSINSTALLDIR%\SDK\v2.0\symbols에 설치됩니다. **확인**을 선택합니다.

   두 번째 방법으로 mscoree.dll 및 mscorwks.dll에 대한 PDB를 Microsoft 기호 서버에서 다운로드할 수 있습니다. 기호 서버를 구성하려면 기호 검색 경로 옵션 대화 상자를 엽니다. **도구** 메뉴에서 **옵션**을 선택 합니다. **옵션** 대화 상자의 왼쪽 창에서 **디버깅** 노드를 열고 **기호**를 선택 합니다. 검색 목록에이 검색 경로를 추가 `https://msdl.microsoft.com/download/symbols` 합니다. 기호 서버 캐시 텍스트 상자에 기호 캐시 디렉터리를 추가한 다음 **확인**을 선택합니다.

1. 디버거 모드를 네이티브 전용 모드로 설정합니다.

   솔루션의 시작 프로젝트에 대 한 **속성** 표를 엽니다. **구성 속성** > **디버깅**을 선택합니다. **디버거 형식** 속성을 **네이티브 전용**으로 설정 합니다.

1. 디버거를 시작 합니다 (F5).

1. **`/clr`** 진단이 생성 되 면 **다시 시도** 를 선택한 후 **중단**을 선택 합니다.

1. 호출 스택 창을 엽니다. 메뉴 모음에서 **디버그**  >  를 선택 합니다. **Windows**  >  **호출 스택입니다**.) 잘못 된 `DllMain` 이니셜라이저 또는 정적 이니셜라이저는 녹색 화살표로 식별 됩니다. 잘못 된 함수가 식별 되지 않은 경우이를 찾으려면 다음 단계를 수행 해야 합니다.

1. 메뉴 모음에서 창 직접 **디버그**를 선택 하 여 **직접 실행** 창을 엽니다  >  **Windows**  >  **Immediate**.

1. `.load sos.dll` **직접 실행** 창에를 입력 하 여 SOS 디버깅 서비스를 로드 합니다.

1. `!dumpstack` **직접 실행** 창에를 입력 하 여 내부 스택의 전체 목록을 가져옵니다 **`/clr`** .

1. _CorDllMain (오류의 원인이 되는 경우) `DllMain` 또는 _VTableBootstrapThunkInitHelperStub 또는 GetTargetForVTableEntry (정적 이니셜라이저가 문제를 발생 시킨 경우) 중 하나 (스택의 맨 아래에 가장 근접)를 찾습니다. 이 호출 바로 아래에 있는 스택 항목이 로더 잠금 상태에서 실행하려 했던 MSIL 구현 함수의 호출입니다.

1. 이전 단계에서 확인 한 소스 파일 및 줄 번호로 이동 하 고 시나리오 섹션에서 설명 하는 시나리오 및 솔루션을 사용 하 여 문제를 해결 합니다.

## <a name="example"></a>예제

### <a name="description"></a>Description

다음 샘플에서는 코드를에서 `DllMain` 전역 개체의 생성자로 이동 하 여 로더 잠금을 방지 하는 방법을 보여 줍니다.

이 샘플에는 원래에서 관리 되는 개체를 포함 하는 생성자가 있는 전역 관리 개체가 있습니다 `DllMain` . 이 샘플의 두 번째 부분에서는 어셈블리를 참조 하 여 초기화를 수행 하는 모듈 생성자를 호출 하는 관리 되는 개체의 인스턴스를 만듭니다.

### <a name="code"></a>코드

```cpp
// initializing_mixed_assemblies.cpp
// compile with: /clr /LD
#pragma once
#include <stdio.h>
#include <windows.h>
struct __declspec(dllexport) A {
   A() {
      System::Console::WriteLine("Module ctor initializing based on global instance of class.\n");
   }

   void Test() {
      printf_s("Test called so linker doesn't throw away unused object.\n");
   }
};

#pragma unmanaged
// Global instance of object
A obj;

extern "C"
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved) {
   // Remove all managed code from here and put it in constructor of A.
   return true;
}
```

이 예제에서는 혼합 어셈블리를 초기화할 때 발생 하는 문제를 보여 줍니다.

```cpp
// initializing_mixed_assemblies_2.cpp
// compile with: /clr initializing_mixed_assemblies.lib
#include <windows.h>
using namespace System;
#include <stdio.h>
#using "initializing_mixed_assemblies.dll"
struct __declspec(dllimport) A {
   void Test();
};

int main() {
   A obj;
   obj.Test();
}
```

이 코드의 결과는 다음과 같습니다.

```Output
Module ctor initializing based on global instance of class.

Test called so linker doesn't throw away unused object.
```

## <a name="see-also"></a>참고 항목

[혼합형 (네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md)
