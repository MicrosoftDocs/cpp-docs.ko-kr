---
title: 혼합형된 어셈블리 초기화 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ba9f3143fb110b25f384e462e7dfcd69c0140802
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439577"
---
# <a name="initialization-of-mixed-assemblies"></a>혼합형 어셈블리 초기화

Windows 개발자가 항상 조심 하십시오 로더 잠금 하는 동안 코드를 실행할 때 `DllMain`합니다. 그러나 C +를 다룰 때 고려해 야 하는 일부 추가적인 고려 사항이 있습니다. + clr 혼합 모드 어셈블리입니다.

내 코드 [DllMain](/windows/desktop/Dlls/dllmain) CLR을 액세스 하지 않아야 합니다. 즉, `DllMain` 은 관리되는 함수를 직접적으로든 간접적으로든 호출하지 않아야 하고, `DllMain`에서 관리 코드를 선언하거나 구현하지 않아야 하며, `DllMain`내에서 가비지 수집이나 자동 라이브러리 로드를 수행하지 않아야 합니다.

## <a name="causes-of-loader-lock"></a>로더 잠금 원인

.NET 플랫폼이 개발되면서 실행 모듈(EXE 또는 DLL)을 로드하는 데 서로 다른 두 가지 메커니즘이 사용되기 시작했습니다. 그 중 하나는 Windows용으로 관리되는 모듈에 사용되고, 다른 하나는 .NET 어셈블리를 로드하는 .NET CLR(공용 언어 런타임)에 사용됩니다. 혼합 DLL 로드 문제는 Microsoft Windows OS 로더에 주로 관련된 것입니다.

.NET 구조체만 포함된 어셈블리를 프로세스에 로드하는 경우에는 필요한 로드 및 초기화 작업을 CLR 로더에서 모두 직접 수행할 수 있습니다. 그러나 혼합형 어셈블리의 경우 네이티브 코드와 데이터가 포함될 수 있으므로 Windows 로더도 함께 사용해야 합니다.

Windows 로더를 사용하면 DLL을 완전히 초기화하기 전에 어떠한 코드에서도 이 DLL의 코드나 데이터에 액세스할 수 없고 DLL이 부분적으로 초기화된 상태에서 어떠한 코드도 이 DLL을 중복하여 다시 로드할 수 없습니다. 이를 위해 Windows 로더에서는 모듈을 초기화하는 동안 안전하지 않은 액세스를 거부하는 프로세스 전역 임계 영역("로더 잠금")을 사용합니다. 따라서 로드 프로세스는 기존의 여러 교착 시나리오에 취약합니다. 혼합형 어셈블리의 경우 다음과 같은 두 가지 시나리오에서 특히 교착 상태의 위험이 증가합니다.

- 첫째, `DllMain` 또는 정적 이니셜라이저 등에서 로더 잠금 상태가 유지되는 동안 사용자가 MSIL(Microsoft Intermediate Language)로 컴파일된 함수를 실행하려고 하면 교착 상태가 발생할 수 있습니다. MSIL 함수에서 로드되지 않은 어셈블리의 형식을 참조하는 경우가 있기 때문입니다. CLR은 이 어셈블리를 자동으로 로드하려고 하며, 이를 위해서는 Windows 로더에서 로드 잠금을 걸어야 합니다. 코드의 호출 시퀀스에서 이미 로더 잠금이 유지되고 있으므로 교착 상태가 발생합니다. 그러나 로더 잠금 상태에서 MSIL을 실행할 때 반드시 교착 상태가 발생하는 것은 아니므로 이 시나리오를 진단하고 수정하기는 쉽지 않습니다. 참조되는 형식의 DLL 및 모든 해당 종속 항목에 네이티브 구문이 들어 있지 않은 경우와 같은 일부 상황에서는 Windows 로더에서 참조되는 형식의 .NET 어셈블리를 로드할 필요가 없습니다. 또한 필수 어셈블리나 해당 혼합 네이티브/.NET 종속 항목이 이미 다른 코드를 통해 로드되었을 수도 있습니다. 따라서 교착 상태는 예측하기가 매우 어려우며 대상 컴퓨터의 구성에 따라 크게 달라질 수 있습니다.

- 둘째, .NET Framework의 버전 1.0 및 1.1에서 DLL을 로드하는 경우 CLR에서는 로더 잠금이 발생하지 않았다고 간주하고 로더 잠금 상태에서는 유효하지 않은 여러 가지 작업을 수행합니다. 순수 .NET DLL의 경우에는 로더 잠금이 발생하지 않았다고 가정하는 데 문제가 없지만, 혼합 DLL은 네이티브 초기화 루틴을 실행하므로 네이티브 Windows 로더가 필요하며 이 때문에 로더 잠금이 발생합니다. 따라서 개발자가 DLL 초기화 과정에서 MSIL 함수를 실행하려고 시도하지 않더라도 .NET Framework의 버전 1.0 및 1.1에서는 불명확한 교착 상태가 발생할 가능성이 있습니다.

혼합 DLL 로드 프로세스의 모든 불명확한 요소가 제거되었습니다. 이는 다음과 같은 변경을 통해 이루어졌습니다.

- CLR이 혼합 DLL을 로드할 때 잘못된 가정을 내리지 않습니다.

- 관리되지 않는 초기화와 관리되는 초기화를 서로 다른 두 단계에서 수행합니다. 관리되지 않는 초기화가 DllMain을 통해 먼저 진행되고, 관리되는 초기화는 *.cctor*이라는 .NET 지원 구조체를 통해 나중에 진행됩니다. **/Zl** 또는 **/NODEFAULTLIB** 를 사용하지 않으면 두 번째 단계가 사용자에게 완전히 노출됩니다. 자세한 내용은[/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md) 및 [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) 를 참조하세요.

로더 잠금이 여전히 발생할 수 있지만 이제 잠금이 일정하게 발생하며 이를 감지할 수 있습니다. 하는 경우 `DllMain` MSIL 명령이 포함 되어 경고를 생성 하는 컴파일러 [컴파일러 경고 (수준 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)합니다. 또한 CRT 또는 CLR에서는 로더 잠금 상황에서 MSIL을 실행하려는 시도를 감지 및 보고합니다. CRT에서 이러한 상황이 감지되면 런타임 진단 C 런타임 오류 R6033이 발생합니다.

이 문서의 나머지 부분에서는 로더 잠금 상태에서 MSIL을 실행할 수 있는 다른 시나리오와 이러한 각 시나리오에서 발생하는 문제에 대한 해결책 및 디버깅 기술에 대해 설명합니다.

## <a name="scenarios-and-workarounds"></a>시나리오 및 해결 방법

로더 잠금 상태에서 사용자 코드가 MSIL을 실행할 수 있는 상황에는 여러 가지가 있습니다. 개발자는 이러한 상황에서 사용자 코드 구현이 MSIL 명령을 실행하지 않도록 주의해야 합니다. 다음 각 하위 섹션에서는 가능한 모든 상황과 가장 일반적인 경우에 발생하는 문제를 해결하는 방법에 대해 설명합니다.

### <a name="dllmain"></a>DllMain

`DllMain` 함수는 DLL에 대한 사용자 정의 진입점입니다. 사용자가 별도로 지정하지 않으면 프로세스나 스레드를 포함 DLL에 연결하거나 해당 DLL에서 분리할 때마다 `DllMain` 이 호출됩니다. 이러한 호출은 로더 잠금 상태에서 발생할 수 있으므로 사용자가 제공한 `DllMain` 함수를 MSI로 컴파일하지 않아야 합니다. 또한 루트가 `DllMain` 에 있는 호출 트리의 어떠한 함수도 MSIL로 컴파일할 수 없습니다. 이 문제를 해결하려면 `DllMain` 을 정의하는 코드 블록을 #pragma `unmanaged`를 사용하여 한정해야 합니다. `DllMain` 을 호출하는 모든 함수에 대해 동일한 작업을 수행해야 합니다.

다른 호출 컨텍스트에서 이러한 함수가 MSIL 구현이 필요한 함수를 호출해야 하는 경우 복제 전략을 사용하여 동일한 함수의 .NET 버전과 네이티브 버전을 모두 만들 수 있습니다.

또는 `DllMain` 이 반드시 필요하지 않거나 로더 잠금 상태에서 실행할 필요가 없는 경우 사용자가 제공한 `DllMain` 구현을 제거하여 문제를 해결할 수 있습니다.

DllMain에서 MSIL을 직접 실행하려고 하면 [Compiler Warning (level 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) 이 발생합니다. 그러나 MSIL을 실행하려는 다른 모듈의 함수를 DllMain이 호출하는 경우에는 컴파일러에서 이를 감지할 수 없습니다.

이 시나리오에 대한 자세한 내용은 "진단 장애 요소"를 참조하세요.

### <a name="initializing-static-objects"></a>정적 개체 초기화

동적 이니셜라이저가 필요한 경우 정적 개체를 초기화하면 교착 상태가 발생할 수 있습니다. 컴파일 타임에 알려진 값으로 정적 변수를 할당하는 경우와 같은 간단한 상황에서는 동적 초기화가 필요하지 않으므로 교착 상태의 위험이 없습니다. 그러나 컴파일 타임에 확인할 수 없는 식, 생성자 호출 또는 함수 호출을 통해 정적 변수를 초기화하는 경우에는 모듈 초기화 과정에서 코드를 실행해야 합니다.

아래 코드에서는 함수 호출, 개체 생성 및 포인터 초기화 같이 동적 초기화가 필요한 정적 이니셜라이저의 예를 보여 줍니다. 이러한 예제는 정적이 아니지만 전역 범위에 정의해야 하는 것으로 간주되므로 결과는 동일합니다.

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

교착 상태가 발생할 가능성은 포함하는 모듈이 **/clr** 로 컴파일되는지 여부와 MSIL이 실행되는지 여부에 따라 달라집니다. 특히 정적 변수가 **/clr** 을 사용하지 않고 컴파일되거나 `unmanaged` 블록 안에 있는 경우 정적 변수를 초기화하는 데 필요한 동적 이니셜라이저에서 MSIL 명령을 실행하게 되므로 교착 상태가 발생할 수 있습니다. 그 이유는 **/clr**을 사용하지 않고 컴파일된 모듈의 경우 DllMain에서 정적 변수를 초기화하기 때문입니다. 반면, **/clr** 을 사용하여 컴파일된 정적 변수는 관리되지 않는 초기화 단계가 완료되고 로더 잠금이 해제된 후에 .cctor에서 초기화됩니다.

정적 변수의 동적 초기화로 인해 발생하는 교착 상태를 해결하는 데는 여러 가지 방법이 있으며, 아래에는 문제를 해결하는 데 걸리는 대략적인 시간 순서에 따라 각 방법이 나열되어 있습니다.

- 정적 변수가 포함된 소스 파일을 **/clr**을 사용하여 컴파일할 수 있습니다.

- 정적 변수를 통해 호출되는 모든 함수를 #pragma `unmanaged` 지시문을 사용하여 네이티브 코드로 컴파일할 수 있습니다.

- 정적 변수가 의존하는 코드를 수동으로 복제하여 .NET 버전과 네이티브 버전에 서로 다른 이름을 지정합니다. 그런 다음 개발자는 네이티브 정적 이니셜라이저에서 네이티브 버전을 호출하고 .NET 버전은 다른 위치에서 호출할 수 있습니다.

### <a name="user-supplied-functions-affecting-startup"></a>시작에 영향을 주는 사용자 제공 함수

시작 시 초기화를 위하여 라이브러리가 의존하는 사용자 제공 함수에는 여러 가지 있습니다. 예를 들어, 전 세계와 같은 c + +에서 연산자를 오버 로드할 때 합니다 `new` 및 `delete` c + + 표준 라이브러리 초기화 및 소멸에 포함 연산자, 사용자가 제공한 버전 어디서 든 사용 합니다. 결과적으로, c + + 표준 라이브러리 및 사용자 제공 정적 이니셜라이저는 이러한 연산자의 모든 사용자 제공 버전을 호출 합니다.

사용자 제공 버전을 MSIL로 컴파일하는 경우 이러한 이니셜라이저는 로더 잠금 상태에서도 MSIL 명령을 실행하려 합니다. 사용자가 제공한 `malloc` 동일한 결과가 발생 합니다. 이 문제를 해결하려면 이러한 오버로드나 사용자 제공 정의를 모두 #pragma `unmanaged` 지시문을 사용하여 네이티브 코드로 구현해야 합니다.

이 시나리오에 대한 자세한 내용은 "진단 장애 요소"를 참조하세요.

### <a name="custom-locales"></a>사용자 지정 로캘

사용자가 사용자 지정 전역 로캘을 제공하는 경우 이 로캘은 정적으로 초기화된 스트림을 비롯하여 이후의 모든 I/O 스트림을 초기화하는 데 사용됩니다. 이 전역 로캘 개체를 MSIL로 컴파일하는 경우 MSIL로 컴파일된 로캘 개체 멤버 함수가 로더 잠금 상태에서 호출될 수 있습니다.

이 문제를 해결하는 데는 세 가지 방법이 있습니다.

모든 전역 I/O 스트림 정의가 포함된 소스 파일을 **/clr** 옵션을 사용하여 컴파일할 수 있습니다. 이렇게 하면 해당 정적 이니셜라이저가 로더 잠금 상태에서 실행되는 것을 막을 수 있습니다.

사용자 지정 로캘 함수 정의를 #pragma `unmanaged` 지시문을 사용하여 네이티브 코드로 컴파일할 수 있습니다.

사용자 지정 로캘을 전역 로캘로 설정하는 것을 로더 잠금이 해제될 때까지 뒤로 미룹니다. 그런 다음 사용자 지정 로캘을 사용하여 초기화할 때 작성된 I/O 스트림을 명시적으로 구성합니다.

## <a name="impediments-to-diagnosis"></a>진단 장애 요소

경우에 따라서는 교착 상태의 원인을 파악하기가 어렵습니다. 다음 하위 섹션에서는 이와 관련된 시나리오 및 이러한 문제를 해결하는 방법에 대해 설명합니다.

### <a name="implementation-in-headers"></a>헤더의 구현

특수한 몇 가지 경우 헤더 파일 내의 함수 구현으로 인해 진단이 어려워질 수 있습니다. 인라인 함수와 템플릿 코드는 모두 헤더 파일에 해당 함수를 지정해야 합니다.  C++ 언어는 이름이 동일한 모든 함수 구현을 의미론적으로 동일하게 파악하는 단일 정의 규칙을 사용합니다. 따라서 C++ 링커에서는 특정 함수의 구현이 중복된 개체 파일을 병합할 때 별다른 사항을 고려할 필요가 없습니다.

Visual Studio 2005 이전 링커는 단순히 다른 소스 파일에 대 한 다른 최적화 옵션을 사용할 경우 정방향 선언 및 시나리오를 수용 하기 위해 이러한 의미상 동등한 정의의 가장 큰를 선택 합니다. 이 경우 혼합 네이티브/.NET DLL에서 문제가 발생합니다.

동일한 헤더가 있을 수 있으므로 c + + 파일에 모두 포함 **/clr** 설정 및 해제 된, 또는 #include #pragma 내에 래핑될 수 `unmanaged` 블록 MSIL 버전과 네이티브 버전이 제공 하는 함수를 모두 할 수 헤더에 구현 합니다. MSIL과 네이티브 구현은 로드 잠금 상태에서의 초기화라는 측면에서 볼 때 의미론이 서로 다르므로 결과적으로 단일 정의 규칙을 위반하게 됩니다. 따라서 링커가 가장 큰 구현을 선택할 때 MSIL 버전의 함수를 선택할 수 있지만 실제로 이는 다른 곳에서 #pragma unmanaged 지시문을 사용하여 네이티브 코드로 명시적으로 컴파일되었을 수 있습니다. 로더 잠금 상태에서 MSIL 버전의 템플릿이나 인라인 함수가 호출되지 않게 하려면 로더 잠금 상태에서 호출되는 이러한 모든 함수의 정의를 모두 #pragma `unmanaged` 지시문으로 한정해야 합니다. 타사 헤더 파일을 사용하는 경우 이를 수행하는 가장 쉬운 방법은 문제가 되는 헤더 파일에 대한 #include 지시문 주위에 #pragma unmanaged 지시문을 배치하는 것입니다. (참조 [관리 되는, 관리 되지 않는](../preprocessor/managed-unmanaged.md) 예입니다.) 그러나 .NET API를 직접 호출해야 하는 다른 코드가 들어 있는 헤더에 대해서는 이 방법을 사용할 수 없습니다.

로더 잠금 문제를 해결하려는 사용자의 편의를 위해 네이티브 구현과 관리되는 구현이 둘 다 있으면 링커에서 네이티브 구현을 선택합니다. 따라서 위와 같은 문제가 발생하지 않습니다. 그러나 이 릴리스에는 컴파일러에서 해결되지 않은 두 가지 문제로 인해 이 규칙에 두 가지 예외가 있습니다.

- 전역 정적 함수 포인터를 통해 인라인 함수를 호출하게 됩니다. 가상 함수는 전역 함수 포인터를 통해 호출되므로 이 시나리오가 특히 두드러집니다. 예를 들어 개체에 적용된

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

로드 잠금 문제에 대한 진단은 모두 디버그 빌드에서 수행해야 합니다. 릴리스 빌드에서는 진단 결과가 생성되지 않을 수 있고 릴리스 모드에서 수행한 최적화로 인해 로더 잠금 시나리오에서 일부 MSIL이 마스크될 수 있습니다.

## <a name="how-to-debug-loader-lock-issues"></a>로더 잠금 문제를 디버깅하는 방법

MSIL 함수를 호출할 때 CLR에서 진단이 생성되면 CLR 실행이 일시 중단됩니다. 한편 디버기 프로세스를 실행 중인 경우 Visual C++ 혼합 모드 디버거가 일시 중단됩니다. 그러나 프로세스에 연결하려 하면 혼합 디버거를 사용하여 디버기에 대한 관리되는 호출 스택을 얻을 수 없습니다.

로더 잠금 상황에서 호출된 특정 MSIL 함수를 식별하려면 다음 단계를 수행해야 합니다.

1. mscoree.dll 및 mscorwks.dll에 대한 기호를 사용할 수 있는지 확인합니다.

   이 작업은 다음 두 가지 방법으로 수행할 수 있습니다. 첫 번째 방법으로 mscoree.dll 및 mscorwks.dll에 대한 PDB를 기호 검색 경로에 추가할 수 있습니다. 이렇게 하려면 기호 검색 경로 옵션 대화 상자를 열어야 합니다. (에서 합니다 **도구** 메뉴 선택 **옵션**합니다. 왼쪽된 창에서를 **옵션** 대화 상자를 열고 합니다 **디버깅** 노드 선택 **기호**.) mscoree.dll 및 mscorwks.dll PDB 파일의 경로를 검색 목록에 추가합니다. 이러한 PDB는 %VSINSTALLDIR%\SDK\v2.0\symbols에 설치됩니다. **확인**을 선택합니다.

   두 번째 방법으로 mscoree.dll 및 mscorwks.dll에 대한 PDB를 Microsoft 기호 서버에서 다운로드할 수 있습니다. 기호 서버를 구성하려면 기호 검색 경로 옵션 대화 상자를 엽니다. (에서 합니다 **도구** 메뉴 선택 **옵션**합니다. 왼쪽된 창에서를 **옵션** 대화 상자를 열고 합니다 **디버깅** 노드 선택 **기호**.) 검색 목록에 다음 검색 경로 추가 합니다. http://msdl.microsoft.com/download/symbols합니다. 기호 서버 캐시 텍스트 상자에 기호 캐시 디렉터리를 추가한 다음 **확인**을 선택합니다.

1. 디버거 모드를 네이티브 전용 모드로 설정합니다.

   이 작업을 수행 하려면 엽니다는 **속성** 솔루션에서 시작 프로젝트에 대 한 표입니다. 선택 **구성 속성** > **디버깅**합니다. 설정 된 **디버거 형식** 하 **네이티브 전용**합니다.

1. F5 키를 눌러 디버거를 시작 합니다.

1. 경우는 **/clr** 진단 생성 되는 경우 선택 **을 다시 시도 하세요** 를 선택한 후 **중단**합니다.

1. 호출 스택 창을 엽니다. (메뉴 모음에서 선택 **디버깅할** > **Windows** > **호출 스택**.) 잘못 된 `DllMain` 또는 정적 이니셜라이저는 녹색 화살표를 사용 하 여 식별 됩니다. 위반하는 함수를 식별할 수 없으면 다음 단계를 수행하여 이를 찾아야 합니다.

1. 엽니다는 **직접 실행** 창 (메뉴 모음에서 **디버그** > **Windows** > **즉시**.)

1. 에.load sos.dll을 입력 합니다 **직접 실행** SOS 디버깅 서비스를 로드 하는 창입니다.

1. 형식! dumpstack을 **직접 실행** 내부의 전체 목록을 가져오기 위해 창을 **/clr** 스택.

1. _Cordllmain (스택 맨 아래에 가장 가까운) 첫 번째 인스턴스를 찾습니다 (경우 `DllMain` 문제를 일으키는), _VTableBootstrapThunkInitHelperStub 또는 GetTargetForVTableEntry (정적 이니셜라이저는 문제를 일으키는) 경우입니다. 이 호출 바로 아래에 있는 스택 항목이 로더 잠금 상태에서 실행하려 했던 MSIL 구현 함수의 호출입니다.

1. 소스 파일을 이동 하 고 시나리오 및 시나리오 섹션에 설명 된 솔루션을 사용 하 여 문제가 있는 줄 번호는 이전 단계에서 확인 하 고 올바른 키를 누릅니다.

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 샘플 코드를 이동 하 여 로더 잠금을 방지 하는 방법을 보여 줍니다 `DllMain` 전역 개체의 생성자에 있습니다.

이 샘플에는 전역 관리 되는 개체의 생성자에서 원래 관리 되는 개체가 포함 `DllMain`합니다. 이 샘플의 두 번째 부분에서는 어셈블리를 참조하고 관리되는 개체의 인스턴스를 만들어 초기화를 수행하는 모듈 생성자를 호출합니다.

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
      printf_s("Test called so linker does not throw away unused object.\n");
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

이 예에서는 혼합된 어셈블리 초기화의 문제를 보여 줍니다.

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

Test called so linker does not throw away unused object.
```

## <a name="see-also"></a>참고자료

[혼합형(네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md)
