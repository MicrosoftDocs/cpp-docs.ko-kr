---
description: '자세한 정보: 방법:/clr로 마이그레이션'
title: '방법: -clr로 마이그레이션'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
ms.openlocfilehash: 39853f755074a4999f39f9e04445234abfbe93b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286399"
---
# <a name="how-to-migrate-to-clr"></a>방법: /clr로 마이그레이션

이 항목에서는 **/clr** 을 사용 하 여 네이티브 코드를 컴파일할 때 발생 하는 문제에 대해 설명 합니다 (자세한 내용은 [/Clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md) 참조). **/clr** 을 사용 하면 네이티브 c + + 코드를 호출 하 고 .net 어셈블리에서 다른 네이티브 c + + 코드를 호출할 수 있습니다. **/Clr** 을 사용 하 여 컴파일하는 이점에 대 한 자세한 내용은 [혼합형 (네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md) 및 [네이티브 및 .net 상호 운용성](../dotnet/native-and-dotnet-interoperability.md) 을 참조 하세요.

## <a name="known-issues-compiling-library-projects-with-clr"></a>/Clr을 사용 하 여 라이브러리 프로젝트를 컴파일하는 알려진 문제

Visual Studio는 **/clr** 을 사용 하 여 라이브러리 프로젝트를 컴파일할 때 알려진 몇 가지 문제를 포함 합니다.

- 코드는 [CRuntimeClass:: FromName](../mfc/reference/cruntimeclass-structure.md#fromname)을 사용 하 여 런타임에 형식을 쿼리할 수 있습니다. 그러나 형식이 MSIL .dll ( **/clr** 을 사용 하 여 컴파일)에 있는 경우에 대 한 호출은 `FromName` 관리 되는 .dll에서 정적 생성자가 실행 되기 전에 발생 하면 실패할 수 있습니다. 즉, 코드를 관리 되는 .dll에서 실행 한 후에는 fromname 호출이 발생 해도이 문제가 표시 되지 않습니다. 이 문제를 해결 하기 위해 관리 되는 .dll에서 함수를 정의 하 고 내보내고 네이티브 MFC 응용 프로그램에서 호출 하 여 관리 되는 정적 생성자를 강제로 생성할 수 있습니다. 예를 들어:

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Visual C++로 컴파일

프로젝트의 모든 모듈에서 **/clr** 을 사용 하기 전에 먼저 Visual Studio 2010을 사용 하 여 네이티브 프로젝트를 컴파일하고 연결 합니다.

다음 단계는 순서 대로 **/clr** 컴파일에 가장 쉬운 경로를 제공 합니다. 이러한 각 단계를 수행 하 고 나면 프로젝트를 컴파일하고 실행 하는 것이 중요 합니다.

### <a name="versions-prior-to-visual-studio-2003"></a>Visual Studio 2003 이전 버전

Visual Studio 2003 이전 버전에서 Visual Studio 2010로 업그레이드 하는 경우 Visual Studio의 향상 된 c + + 표준 규칙과 관련 된 컴파일러 오류가 표시 될 수 있습니다. 2003

### <a name="upgrading-from-visual-studio-2003"></a>Visual Studio 2003에서 업그레이드

이제 visual studio 2003을 사용 하 여 빌드한 프로젝트를 먼저 **/clr** 없이 컴파일해야 합니다. 이제 visual STUDIO는 ANSI/ISO 규격 및 일부 주요 변경 사항을 향상 시켰습니다. 가장 주목 해야 할 가능성이 높은 변경 내용은 [CRT의 보안 기능](../c-runtime-library/security-features-in-the-crt.md)입니다. CRT를 사용 하는 코드는 사용 중단 경고를 생성할 가능성이 매우 높습니다. 이러한 경고는 표시 되지 않지만, 향상 된 보안 기능을 제공 하 고 코드의 보안 문제를 표시할 수 있으므로 새로운 [보안 강화 버전의 CRT 함수로](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) 마이그레이션해야 합니다.

### <a name="upgrading-from-managed-extensions-for-c"></a>Managed Extensions for C++에서 업그레이드

Visual Studio 2005부터 Managed Extensions for C++로 작성 된 코드는 **/clr** 에서 컴파일되지 않습니다.

## <a name="convert-c-code-to-c"></a>C 코드를 c + +로 변환

Visual Studio는 C 파일을 컴파일하도록 하지만 **/clr** 컴파일을 위해 c + +로 변환 해야 합니다. 실제 파일 이름을 변경할 필요가 없습니다. **/tp** ( [/tc,/tp,/tc,/Tp (소스 파일 형식 지정)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)참조)를 사용할 수 있습니다. **/Clr** 에는 c + + 소스 코드 파일이 필요 하지만 개체 지향 패러다임을 사용 하도록 코드를 다시 사용할 필요는 없습니다.

C 코드는 c + + 파일로 컴파일될 때 변경 해야 할 가능성이 매우 높습니다. C + + 형식 안전 규칙은 엄격한 규칙 이므로 캐스트를 사용 하 여 명시적으로 형식을 변환 해야 합니다. 예를 들어 malloc는 void 포인터를 반환 하지만 캐스트를 사용 하 여 C의 모든 형식에 대 한 포인터에 할당할 수 있습니다.

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

또한 함수 포인터는 c + +에서 엄격 하 게 형식이 안전 하므로 다음 C 코드를 수정 해야 합니다. C + +에서는 **`typedef`** 함수 포인터 형식을 정의 하는를 만든 다음 해당 형식을 사용 하 여 함수 포인터를 캐스팅 하는 것이 가장 좋습니다.

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

또한 c + +에서는 함수를 참조 하거나 호출 하기 전에 해당 함수를 프로토타입화 하거나 완전히 정의 해야 합니다.

C + +에서 키워드 (예:,,,,, 등)로 발생 하는 c 코드에서 사용 되는 식별자 **`virtual`** **`new`** **`delete`** **`bool`** **`true`** **`false`** 의 이름을 바꿔야 합니다. 일반적으로이 작업은 간단한 검색 및 바꾸기 작업으로 수행할 수 있습니다.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>프로젝트 설정 다시 구성

Visual Studio 2010에서 프로젝트를 컴파일하고 실행 한 후에는 기본 구성을 수정 하는 대신 **/clr** 에 대 한 새 프로젝트 구성을 만들어야 합니다. **/clr** 은 일부 컴파일러 옵션과 호환 되지 않으며, 개별 구성을 만들면 프로젝트를 네이티브 또는 관리로 빌드할 수 있습니다. 속성 페이지 대화 상자에서 **/clr** 을 선택 **하는 경우/clr과 호환** 되지 않는 프로젝트 설정이 비활성화 됩니다. **/clr** 이 이후에 선택 취소 된 경우 비활성화 된 옵션은 자동으로 복원 되지 않습니다.

### <a name="create-new-project-configurations"></a>새 프로젝트 구성 만들기

**새 프로젝트 구성 대화 상자** (**빌드** Configuration Manager 활성 솔루션 구성 새로 만들기)에서 **설정 복사** 옵션을 사용  >    >    >  하 여 기존 프로젝트 설정에 따라 프로젝트 구성을 만들 수 있습니다. 디버그 구성에 대해이 작업을 한 번 수행 하 고 릴리스 구성에 대해 한 번 수행 합니다. 이후 변경 내용은 **/clr** 관련 구성에만 적용 될 수 있으며 원래 프로젝트 구성은 그대로 유지 됩니다.

사용자 지정 빌드 규칙을 사용 하는 프로젝트에는 추가 주의가 필요할 수 있습니다.

이 단계는 메이크파일을 사용 하는 프로젝트에 대해 서로 다른 의미를 갖습니다. 이 경우 별도의 빌드 대상을 구성 하거나, 원본의 복사본에서 **/clr** 컴파일과 관련 된 버전을 만들 수 있습니다.

### <a name="change-project-settings"></a>프로젝트 설정 변경

/clr [(공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)의 지침에 따라 개발 환경에서 **/clr** 을 선택할 수 있습니다. 앞에서 설명한 것 처럼이 단계는 충돌 하는 프로젝트 설정을 자동으로 사용 하지 않도록 설정 합니다.

> [!NOTE]
> Visual Studio 2003에서 관리 라이브러리나 웹 서비스 프로젝트를 업그레이드 하는 경우 **/zl** 컴파일러 옵션이 **명령줄** 속성 페이지에 추가 됩니다. 이렇게 하면 LNK2001이 발생 합니다. 확인을 위해 **명령줄** 속성 페이지에서 **/zl** 을 제거 합니다. 자세한 내용은 [/zl (기본 라이브러리 이름 생략)](../build/reference/zl-omit-default-library-name.md) 및 [컴파일러 및 빌드 속성 설정](../build/working-with-project-properties.md) 을 참조 하세요. 또는 msvcrt.lib 및 msvcmrt.lib를 링커의 **추가 종속성** 속성에 추가 합니다.

메이크파일로 빌드된 프로젝트의 경우 **/clr** 을 추가 하면 호환 되지 않는 컴파일러 옵션을 수동으로 사용 하지 않도록 설정 해야 합니다. **/Clr** 과 호환 되지 않는 컴파일러 옵션에 대 한 자세한 내용은/[/clr 제한](../build/reference/clr-restrictions.md) 을 참조 하세요.

### <a name="precompiled-headers"></a>미리 컴파일된 헤더

미리 컴파일된 헤더는 **/clr** 에서 지원 됩니다. 그러나/clr을 사용 하 여 일부 CPP 파일만 컴파일하는 경우 **(rest** 를 네이티브로 컴파일) **/clr** 을 사용 하 여 생성 된 미리 컴파일된 헤더가 **/clr** 을 사용 하지 않고 생성 된 헤더와 호환 되지 않기 때문에 일부 변경이 필요 합니다. 이러한 비 호환성은 **/clr** 에서 메타 데이터를 생성 하 고 요구 하기 때문에 발생 합니다. 따라서 모듈 컴파일 **/clr** 은 메타 데이터를 포함 하지 않는 미리 컴파일된 헤더를 사용할 수 없으며 **/clr** 이 아닌 모듈은 메타 데이터를 포함 하는 미리 컴파일된 헤더 파일을 사용할 수 없습니다.

일부 모듈이 컴파일되는 프로젝트를 **컴파일하는 가장** 쉬운 방법은 미리 컴파일된 헤더를 완전히 사용 하지 않도록 설정 하는 것입니다. (프로젝트 속성 페이지 대화 상자에서 C/c + + 노드를 열고 미리 컴파일된 헤더를 선택 합니다. 그런 다음, 미리 컴파일된 헤더 만들기/사용 속성을 "미리 컴파일된 헤더 사용 안 함"으로 변경 합니다.

그러나 특히 큰 프로젝트의 경우 미리 컴파일된 헤더를 사용 하면 컴파일 속도가 훨씬 우수 하므로이 기능을 사용 하지 않는 것이 좋습니다. 이 경우 별도의 미리 컴파일된 헤더를 사용 하도록 **/clr** 및 비 **/clr** 파일을 구성 하는 것이 가장 좋습니다. 이 작업은 **솔루션 탐색기** 를 사용 하 여 **/clr** 로 컴파일할 모듈을 다중 선택 하 고 그룹을 마우스 오른쪽 단추로 클릭 한 다음 속성을 선택 하 여 한 번에 수행할 수 있습니다. 그런 다음 파일 및 미리 컴파일된 헤더 파일 속성을 사용 하 여 만들기/사용 PCH를 변경 하 여 각각 다른 헤더 파일 이름과 PCH 파일을 사용 합니다.

## <a name="fixing-errors"></a>오류 수정

**/Clr** 을 사용 하 여 컴파일하면 컴파일러, 링커 또는 런타임 오류가 발생할 수 있습니다. 이 섹션에서는 가장 일반적인 문제에 대해 설명 합니다.

### <a name="metadata-merge"></a>메타 데이터 병합

서로 다른 버전의 데이터 형식을 사용할 경우 두 형식에 대해 생성 된 메타 데이터가 일치 하지 않기 때문에 링커가 실패할 수 있습니다. 이 문제는 일반적으로 형식의 멤버가 조건부로 정의 될 때 발생 하지만 해당 형식을 사용 하는 모든 CPP 파일에 대해서는 조건이 동일 하지 않습니다. 이 경우 링커가 실패 하 고 형식이 정의 된 두 번째 OBJ 파일의 이름 및 기호 이름만 보고 합니다. OBJ 파일이 링커에 전달 되는 순서를 회전 하 여 다른 버전의 데이터 형식 위치를 검색 하는 것이 유용한 경우가 많습니다.

### <a name="loader-lock-deadlock"></a>로더 잠금 교착 상태

"로더 잠금 교착 상태"는 발생할 수 있지만 결정적 이며 런타임에 검색 되어 보고 됩니다. 자세한 배경, 지침 및 솔루션은 [혼합 어셈블리 초기화](../dotnet/initialization-of-mixed-assemblies.md) 를 참조 하세요.

### <a name="data-exports"></a>데이터 내보내기

DLL 데이터 내보내기는 오류가 발생 하기 쉬우며 권장 하지 않습니다. Dll의 일부 관리 되는 부분이 실행 될 때까지 DLL의 데이터 섹션이 초기화 되지 않을 수 있기 때문입니다. [#Using 지시어](../preprocessor/hash-using-directive-cpp.md)를 사용 하 여 메타 데이터를 참조 합니다.

### <a name="type-visibility"></a>형식 표시 유형

네이티브 형식은 기본적으로 private입니다. 이로 인해 네이티브 형식이 DLL 외부에서 표시 되지 않을 수 있습니다. 이러한 형식에를 추가 하 여이 오류 **`public`** 를 해결 합니다.

### <a name="floating-point-and-alignment-issues"></a>부동 소수점 및 맞춤 문제

`__controlfp` 는 공용 언어 런타임에서 지원 되지 않습니다 (자세한 내용은 [_control87, _controlfp, \_ _control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) 참조). CLR도 [정렬을](../cpp/align-cpp.md)고려 하지 않습니다.

### <a name="com-initialization"></a>COM 초기화

공용 언어 런타임은 모듈이 초기화 될 때 COM을 자동으로 초기화 합니다 (COM이 자동으로 초기화 되 면 MTA로 수행 됨). 따라서 명시적으로 COM을 초기화 하면 COM이 이미 초기화 되었음을 나타내는 반환 코드가 생성 됩니다. CLR이 이미 COM을 다른 스레딩 모델로 초기화 했을 때 하나의 스레딩 모델을 사용 하 여 COM을 명시적으로 초기화 하려고 하면 응용 프로그램에 오류가 발생할 수 있습니다.

공용 언어 런타임은 기본적으로 COM을 MTA로 시작 합니다. [/CLRTHREADATTRIBUTE (CLR 스레드 특성 설정)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) 을 사용 하 여이를 수정 합니다.

### <a name="performance-issues"></a>성능 이슈

MSIL로 생성 되는 네이티브 c + + 메서드를 간접적으로 호출 하는 경우 성능이 저하 될 수 있습니다 (가상 함수 호출 또는 함수 포인터 사용). 이에 대해 자세히 알아보려면 [이중 썽킹](../dotnet/double-thunking-cpp.md)을 참조 하세요.

네이티브에서 MSIL로 이동할 때 작업 집합의 크기가 증가 하는 것을 알 수 있습니다. 이는 공용 언어 런타임이 프로그램이 올바르게 실행 되도록 하기 위해 많은 기능을 제공 하기 때문입니다. **/Clr** 응용 프로그램이 올바르게 실행 되 고 있지 않은 경우 C4793를 사용 하도록 설정할 수 있습니다 (기본적으로 해제 됨). 자세한 내용은 [컴파일러 경고 (수준 1 및 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) 를 참조 하세요.

### <a name="program-crashes-on-shutdown"></a>종료 시 프로그램 작동 중단

일부 경우에는 관리 코드 실행이 완료 되기 전에 CLR이 종료 될 수 있습니다. 및를 사용 하면 `std::set_terminate` `SIGTERM` 이 문제가 발생할 수 있습니다. 자세한 내용은 [신호 상수](../c-runtime-library/signal-constants.md) 및 [set_terminate](../c-runtime-library/abnormal-termination.md) 을 참조 하세요.

## <a name="using-new-visual-c-features"></a>새 Visual C++ 기능 사용

응용 프로그램을 컴파일하고, 링크 하 고, 실행 한 후 **/clr** 로 컴파일된 모든 모듈에서 .net 기능 사용을 시작할 수 있습니다. 자세한 내용은 [런타임 플랫폼의 구성 요소 확장](../extensions/component-extensions-for-runtime-platforms.md)을 참조하세요.

Visual C++의 .NET 프로그래밍에 대 한 자세한 내용은 다음을 참조 하세요.

- [C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [네이티브 및 .NET 상호 운용성](../dotnet/native-and-dotnet-interoperability.md)

- [런타임 플랫폼용 구성 요소 확장](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>참고 항목

[혼합형 (네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md)
