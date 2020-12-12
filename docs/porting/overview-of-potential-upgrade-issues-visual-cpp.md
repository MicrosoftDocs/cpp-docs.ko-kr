---
description: '자세한 정보: 잠재적인 업그레이드 문제 개요 (Visual C++)'
title: 잠재적인 업그레이드 문제 개요(Visual C++)
ms.date: 05/03/2019
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
ms.openlocfilehash: 42060fc7bd1aeedebf6cdfc7f645ad8eea38153c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115211"
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>잠재적인 업그레이드 문제 개요(Visual C++)

지난 몇 년 동안 C++ 언어 자체, C++ 표준 라이브러리, C 런타임(CRT) 및 MFC, ATL 등의 기타 라이브러리의 변경과 함께 Microsoft C++ 컴파일러에도 많은 변화가 있었습니다. 결과적으로, 이전 버전의 Visual Studio에서 애플리케이션을 업그레이드할 때 이전에는 정상적으로 컴파일된 코드에서 컴파일러 및 링커 오류와 경고가 발생할 수 있습니다. 원래 코드베이스가 오래될수록 이러한 오류 가능성이 커집니다. 이 개요에서는 발생할 수 있는 가장 일반적인 문제 클래스를 요약하고 자세한 정보 링크를 제공합니다.

> [!NOTE]
> 과거에는 여러 버전의 Visual Studio에 걸친 업그레이드를 한 번에 하나씩 증분 방식으로 수행하도록 권장했습니다. 이 방법은 더 이상 권장되지 않습니다. 코드베이스가 아무리 오래되었다 해도 최신 버전의 Visual Studio로 업그레이드하는 것이 더 간단한 경우가 많았습니다.

업그레이드 프로세스와 관련된 질문이나 의견이 있으면 vcupgrade@microsoft.com로 보내주시기 바랍니다.

## <a name="library-and-toolset-dependencies"></a>라이브러리 및 도구 집합 종속성

> [!NOTE]
> 이 섹션은 Visual Studio 2013 및 이전 버전으로 빌드된 애플리케이션 및 라이브러리에 적용됩니다. Visual Studio 2015, Visual Studio 2017 및 Visual Studio 2019에서 사용되는 도구 집합은 이진 호환이 가능합니다. 자세한 내용은 [Visual Studio 2015와 Visual Studio 2019 간의 C++ 이진 호환성](binary-compat-2015-2017.md)을 참조하세요.

애플리케이션을 새 버전의 Visual Studio로 업그레이드하는 경우 애플리케이션이 연결하는 모든 라이브러리와 DLL도 업그레이드하는 것이 좋으며, 대부분의 경우에 필요합니다. 소스 코드에 액세스할 수 있거나, 라이브러리 공급업체가 동일한 주 버전의 컴파일러를 사용하여 컴파일된 새 이진 파일을 제공할 수 있어야 합니다. 이러한 조건 중 하나에 해당하면 이진 호환성의 세부 사항을 처리하는 이 섹션을 건너뛰어도 됩니다. 이 경우에 해당하지 않는 경우 업그레이드된 애플리케이션에서 라이브러리를 사용하지 못할 수 있습니다. 이 섹션의 정보는 업그레이드를 진행할 수 있는지 여부를 이해하는 데 도움이 됩니다.

### <a name="toolset"></a>도구 집합

.obj 및 .lib 파일 형식은 잘 정의되어 있고 거의 변경되지 않습니다. 때때로 이러한 파일 형식이 추가되지만, 일반적으로 이러한 추가 항목은 최신 도구 집합이 이전 도구 집합에서 생성된 개체 파일 및 라이브러리를 사용하는 데 영향을 주지 않습니다. 여기서 중요한 예외는 [/GL(전체 프로그램 최적화)](../build/reference/gl-whole-program-optimization.md)을 사용하여 컴파일하는 경우입니다. `/GL`을 사용하여 컴파일하는 경우 결과로 생성된 개체 파일은 이 파일을 생성하는 데 사용된 것과 동일한 도구 집합을 통해서만 연결할 수 있습니다. 따라서 `/GL` 및 Visual Studio 2017(v141) 컴파일러를 사용하여 개체 파일을 생성하는 경우 Visual Studio 2017(v141) 링커를 사용하여 연결해야 합니다. 개체 파일 내의 내부 데이터 구조가 도구 집합의 주 버전 간에 안정적이지 않으며 최신 도구 집합이 오래된 데이터 형식을 이해하지 못하기 때문입니다.

C++에는 안정적인 ABI(애플리케이션 이진 인터페이스)가 없습니다. 그러나 Visual Studio는 릴리스의 모든 부 버전에 대해 안정적인 C++ ABI를 유지 관리합니다. Visual Studio 2015(v140), Visual Studio 2017(v141) 및 Visual Studio 2019(v142)는 부 버전에서만 달라집니다. 모두 동일한 주 버전 번호인 14를 가지고 있습니다. 자세한 내용은 [Visual Studio 2015와 Visual Studio 2019 간의 C++ 이진 호환성](binary-compat-2015-2017.md)을 참조하세요.

C++ 링크와 함게 외부 기호를 포함하는 개체 파일이 있는 경우 해당 개체 파일은 다른 주 버전의 도구 집합에 의해 생성된 개체 파일과 올바르게 연결되지 않을 수 있습니다. 여러 가능한 결과가 있습니다. 연결이 완전히 실패할 수 있습니다(예: 이름 데코레이션이 변경된 경우). 연결이 성공할 수 있으며 런타임 시 작동하지 않을 수 있습니다(예: 형식 레이아웃이 변경된 경우). 또는 많은 경우에 아무런 작업도 일어나지 않을 수 있습니다. 또한 C++ ABI는 불안정하지만 C ABI 및 COM에 필요한 C++ ABI의 하위 집합은 안정적입니다.

가져오기 라이브러리에 링크하면 런타임 시 ABI 호환성을 유지하는 Visual Studio 재배포 가능 라이브러리의 이후 버전을 사용할 수 있습니다. 예를 들어, Visual Studio 2015 업데이트 3 도구 집합을 사용하여 앱을 컴파일하고 링크한 경우 2015, 2017 및 2019 라이브러리가 이전 버전과의 호환성을 유지했기 때문에 Visual Studio 2017 또는 Visual Studio 2019 재배포 가능 패키지를 사용할 수 있습니다. 반대의 경우는 그렇지 않습니다. 호환 되는 ABI가 있는 경우에도 코드를 빌드하는 데 사용한 것 보다 이전 버전의 도구 집합에 대해 재배포 가능 패키지를 사용할 수 없습니다.

### <a name="libraries"></a>라이브러리

특정 버전의 Visua Studiol C++ 라이브러리 헤더 파일을 사용하여 소스 파일을 컴파일하는 경우(헤더 #including 사용) 결과로 생성된 개체 파일은 동일한 버전의 라이브러리에만 연결해야 합니다. 따라서 예를 들어 소스 파일이 Visual Studio 2015 업데이트 3을 사용 하 여 컴파일되는 경우 \<immintrin.h> Visual studio 2015 업데이트 3 vcruntime 라이브러리와 연결 해야 합니다. 마찬가지로 소스 파일이 Visual Studio 2017 버전 15.5을 사용 하 여 컴파일되는 경우 \<iostream> Visual studio 2017 버전 15.5 표준 c + + 라이브러리 라이브러리인 msvcprt에 연결 해야 합니다. 혼합 및 일치는 지원되지 않습니다.

C++ 표준 라이브러리의 경우 Visual Studio 2010 이후 표준 헤더에서 `#pragma detect_mismatch`를 사용하여 혼합 및 일치가 명시적으로 금지되었습니다. 호환되지 않는 개체 파일이나 잘못된 표준 라이브러리에 연결을 시도하면 연결이 실패합니다.

CRT의 경우 혼합 및 일치가 지원된 적이 없지만, API 화면이 많이 변경되지 않았기 때문에 Visual Studio 2015 및 유니버설 CRT까지 작동하는 경우가 많았습니다. 앞으로 이전 버전과의 호환성을 유지할 수 있도록 유니버설 CRT에서는 이전 버전과의 호환성을 중단했습니다. 즉, 앞으로는 버전이 있는 새 유니버설 CRT 이진을 도입할 계획이 없습니다. 대신, 기존 유니버설 CRT가 현재 위치에서 업데이트됩니다.

이전 버전의 Microsoft C 런타임 헤더를 사용하여 컴파일된 개체 파일(및 라이브러리)과 부분 링크 호환성을 제공하기 위해 Visual Studio 2015 이상에서는 legacy_stdio_definitions.lib 라이브러리가 제공됩니다. 이 라이브러리는 유니버설 CRT에서 제거된 대부분의 함수 및 데이터 내보내기에 대해 호환성 기호를 제공합니다. legacy_stdio_definitions.lib에서 제공하는 호환성 기호 집합은 Windows SDK에 포함된 라이브러리의 모든 종속성을 포함하여 대부분의 종속성을 충족하기에 충분합니다. 그러나 호환성 기능을 제공할 수 없는 유니버설 CRT에서 일부 기호가 제거되었습니다. 이러한 기호로 일부 함수(예: \_\_iob\_func)와 데이터 내보내기(예: \_\_imp\_\_\_iob, \_\_imp\_\_\_pctype, \_\_imp\_\_\_mb\_cur\_max)가 있습니다.

이전 버전의 C 런타임 헤더를 사용하여 빌드된 정적 라이브러리가 있는 경우 다음 작업을 이 순서대로 수행하는 것이 좋습니다.

1. 새로운 버전의 Visual Studio 및 유니버설 CRT 헤더를 사용하여 유니버설 CRT와의 연결을 지원하도록 고정 라이브러리를 다시 빌드합니다. 이 방법은 완벽하게 지원되는 최상의 옵션입니다.

1. 고정 라이브러리를 다시 빌드할 수 없거나 다시 빌드하지 않으려는 경우 legacy\_stdio\_definitions.lib에 연결을 시도할 수 있습니다. 정적 라이브러리의 링크 타임 종속성을 충족하는 경우 이진에서 사용 시 정적 라이브러리를 철저히 테스트하여 [유니버설 CRT에 대한 동작 변경 내용](visual-cpp-change-history-2003-2015.md#BK_CRT)의 영향을 받지 않는지 확인하는 것이 좋습니다.

1. 정적 라이브러리의 종속성이 레거시 stdio.h에서 충족 되지 \_ \_ 않거나, 앞서 언급 한 동작 변경으로 인해 라이브러리가 유니버설 CRT에서 작동 하지 않는 경우, 올바른 버전의 Microsoft C 런타임에 연결 하는 DLL로 정적 라이브러리를 캡슐화 하는 것이 좋습니다. 예를 들어 고정 라이브러리가 Visual Studio 2013을 사용하여 빌드된 경우 Visual Studio 2013과 Visual Studio 2013 C++ 라이브러리를 사용하여 이 DLL을 빌드하는 것이 좋습니다. 라이브러리를 DLL로 빌드하면 특정 버전의 Microsoft C 런타임에 종속성이 있는 구현 세부 정보가 캡슐화됩니다. DLL 경계를 넘어 FILE*을 반환하는 경우나 malloc 할당된 포인터를 반환하고 호출자가 해제할 것으로 기대하는 경우와 같이 DLL 인터페이스에서 사용하는 C 런타임의 세부 정보가 누출되지 않도록 주의하세요.

단일 프로세스에서 여러 CRT를 사용하는 것 자체는 문제가 없습니다. 실제로 대부분의 프로세스는 여러 CRT DLL을 로드하게 됩니다. 예를 들어 Windows 운영 체제 구성 요소는 msvcrt.dll을 사용하고 CLR은 고유한 프라이빗 CRT를 사용합니다. 여러 CRT의 상태를 혼합하면 문제가 발생합니다. 예를 들어 msvcr110.dll!malloc를 사용하여 메모리를 할당하고 msvcr120.dll!free를 사용하여 해당 메모리 할당을 취소해서는 안 되며, msvcr110!fopen을 사용하여 FILE을 열고 msvcr120!fread을 사용하여 해당 FILE에서 읽기를 시도하면 안 됩니다. 다른 CRTs의 상태를 혼합 하지 않는 한 단일 프로세스에서 여러 CRTs를 안전 하 게 로드할 수 있습니다.

자세한 내용은 [코드를 유니버설 CRT로 업그레이드](upgrade-your-code-to-the-universal-crt.md)을 참조하세요.

## <a name="errors-due-to-project-settings"></a>프로젝트 설정으로 인한 오류

업그레이드 프로세스를 시작하려면 최신 버전의 Visual Studio에서 이전 프로젝트/솔루션/작업 영역을 엽니다. Visual Studio는 이전 프로젝트 설정에 따라 새 프로젝트를 만듭니다. 이전 프로젝트에 비표준 위치로 하드 코딩 된 라이브러리 또는 포함 경로가 있는 경우 프로젝트에서 기본 설정을 사용할 때 해당 경로에 있는 파일이 컴파일러에 표시 되지 않을 수 있습니다. 자세한 내용은 [링커 OutputFile 설정](porting-guide-spy-increment.md#linker_output_settings)을 참조하세요.

일반적으로, 프로젝트 유지 관리를 간소화하고 업그레이드된 코드가 최대한 빨리 컴파일되도록 돕기 위해 지금 프로젝트 코드를 제대로 구성하는 것이 좋습니다. 소스 코드가 이미 잘 구성되었으며 이전 프로젝트가 Visual Studio 2010 이상으로 컴파일된 경우 이전 컴파일러와 새 컴파일러 둘 다에서 컴파일을 지원하도록 새 프로젝트 파일을 수동으로 편집할 수 있습니다. 다음 예제에서는 Visual Studio 2015와 Visual Studio 2017 둘 다에 대해 컴파일하는 방법을 보여 줍니다.

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LNK2019: 확인할 수 없는 외부 참조

확인할 수 없는 기호의 경우 프로젝트 설정을 수정해야 할 수 있습니다.

- 원본 파일이 기본 위치가 아닌 위치에 있는 경우 프로젝트의 include 디렉터리에 경로를 추가 했나요?

- 외부 참조가 .lib 파일에서 정의된 경우 프로젝트 속성에서 lib 경로를 지정했으며 해당 위치에 올바른 버전의 .lib 파일이 있나요?

- 다른 버전의 Visual Studio를 사용하여 컴파일된 .lib 파일에 연결하려고 하나요? 그렇다면 라이브러리 및 도구 집합 종속성에 대한 이전 섹션을 참조하세요.

- 호출 사이트의 인수 형식이 함수의 기존 오버로드와 실제로 일치하나요? 함수의 시그니처와 함수를 호출 하는 코드의 형식 정의에 대 한 기본 형식이 필요한 지 확인 합니다.

확인되지 않은 기호 오류를 해결하려면 dumpbin.exe를 사용하여 이진 파일에 정의된 기호를 검사해 볼 수 있습니다. 다음 명령줄을 실행하여 라이브러리에 정의된 기호를 확인해 보세요.

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t(wchar_t를 네이티브 형식으로 인식)

Microsoft Visual C++ 6.0 이전 버전에서는 **`wchar_t`** 가 기본 제공 형식으로 구현 되지 않았지만, wchar에서 부호 없는 short에 대 한 typedef로 선언 되었습니다. C + + 표준에서는 **`wchar_t`** 가 기본 제공 형식 이어야 합니다. typedef 버전을 사용하면 이식성 문제가 발생할 수 있습니다. 이전 버전의 Visual Studio에서 업그레이드 하 고 코드가를로 암시적으로 변환 하려고 하기 때문에 컴파일러 오류 C 2664 발생 한 경우를 설정 하는 **`wchar_t`** **`unsigned short`** 대신 오류를 수정 하는 코드를 변경 하는 것이 좋습니다 `/Zc:wchar_t-` . 자세한 내용은 [/zc: wchar_t (Wchar_t 네이티브 형식)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)를 참조 하세요.

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>/NODEFAULTLIB, /ENTRY 및 /NOENTRY 링커 옵션을 사용하여 업그레이드

`/NODEFAULTLIB` 링커 옵션(또는 모든 기본 라이브러리 무시 링커 속성)은 CRT 등의 기본 라이브러리를 자동으로 연결하지 않도록 링커에 지시합니다. 이는 각 라이브러리가 개별 입력으로 나타나야 합니다. 이 라이브러리 목록은 **프로젝트 속성** 대화 상자의 **링커** 섹션에 있는 **추가 종속성** 속성에서 제공됩니다.

일부 기본 라이브러리의 콘텐츠가 리팩터링되었기 때문에 이 옵션을 사용하는 프로젝트는 업그레이드 시 문제가 발생합니다. **추가 종속성 속성** 이나 링커 명령줄에 각 라이브러리가 나열되어야 하기 때문에 현재 이름을 모두 사용하도록 라이브러리 목록을 업데이트해야 합니다.

다음 표에서는 Visual Studio 2015부터 콘텐츠가 변경된 라이브러리를 보여 줍니다. 업그레이드하려면 첫 번째 열의 라이브러리에 두 번째 열의 이름을 추가해야 합니다. 이러한 라이브러리 중 일부는 가져오기 라이브러리 이지만 중요 하지 않습니다.

|기존 이름|다음 라이브러리를 사용해야 합니다.|
|-|-|
|LIBCMT.lib|libcmt.lib, libucrt.lib, libvcruntime.lib|
|libcmtd.lib|libcmtd.lib, libucrtd.lib, libvcruntimed.lib|
|msvcrt.lib|msvcrt.lib, ucrt.lib, vcruntime.lib|
|msvcrtd.lib|msvcrtd.lib, ucrtd.lib, vcruntimed.lib|

기본 라이브러리를 건너뛰는 효과가 있는 `/ENTRY` 옵션 또는 `/NOENTRY` 옵션을 사용하는 경우에도 같은 문제가 적용됩니다.

## <a name="errors-due-to-improved-language-conformance"></a>향상된 언어 규칙으로 인한 오류

Microsoft C++ 컴파일러는 지난 몇 년 동안 C++ 표준에 대한 규칙을 지속적으로 향상시켜 왔습니다. 이전 버전에서 컴파일된 코드가 Visual Studio에서는 컴파일되지 않을 수 있습니다. 컴파일러가 이전에 무시했거나 명시적으로 허용한 오류를 올바르게 플래그하기 때문입니다.

예를 들어 `/Zc:forScope` 스위치는 MSVC 기록의 초기에 도입되었습니다. 루프 변수에 대해 비준수 동작을 허용합니다. 해당 스위치는 이제 사용되지 않으며 이후 버전에서 제거될 수 있습니다. 코드를 업그레이드하는 경우 해당 스위치를 사용하지 않는 것이 좋습니다. 자세한 내용은 [/Zc:forScope-가 사용되지 않음](porting-guide-spy-increment.md#deprecated_forscope)을 참조하세요.

업그레이드할 때 표시될 수 있는 일반적인 컴파일러 오류 중 한 가지 예는 비 const 인수가 const 매개 변수에 전달되는 경우입니다. 이전 버전의 컴파일러는 항상 오류로 플래그하지 않았습니다. 자세한 내용은 [컴파일러의 보다 엄격한 변환](porting-guide-spy-increment.md#stricter_conversions)을 참조하세요.

특정 규칙 향상에 대한 자세한 내용은 [Visual C++ 변경 기록 2003~2015](visual-cpp-change-history-2003-2015.md) 및 [Visual Studio의 C++ 규칙 향상](../overview/cpp-conformance-improvements.md)을 참조하세요.

## <a name="errors-involving-stdinth-integral-types"></a>\<stdint.h>정수 계열 형식과 관련 된 오류

\<stdint.h>헤더는 기본 제공 정수 계열 형식과 달리 모든 플랫폼에서 지정 된 길이를 갖도록 하는 typedef 및 매크로를 정의 합니다. 예를 들면 `uint32_t` 및 `int64_t`입니다. \<stdint.h>헤더가 Visual Studio 2010에 추가 되었습니다. 2010 이전에 작성 된 코드는 이러한 형식에 대 한 전용 정의를 제공 했을 수 있으며 이러한 정의는 항상 정의와 일치 하지 않을 수 있습니다 \<stdint.h> .

오류가 C2371이고 `stdint` 형식이 관련된 경우 해당 형식이 코드 또는 타사 lib 파일의 헤더에서 정의된 것입니다. 업그레이드할 때 형식의 사용자 지정 정의를 제거 해야 \<stdint.h> 하지만, 먼저 사용자 지정 정의를 현재 표준 정의와 비교 하 여 새로운 문제가 발생 하지 않도록 해야 합니다.

**F12** 키 (**정의로 이동**)를 눌러 해당 형식이 정의 된 위치를 확인할 수 있습니다.

여기서는 [/showIncludes](../build/reference/showincludes-list-include-files.md) 컴파일러 옵션이 유용할 수 있습니다. 프로젝트에 대한 **속성 페이지** 대화 상자에서 **C/C++** > **고급** 페이지를 열고 **포함 표시** 를 **예** 로 설정합니다. 그런 다음, 프로젝트를 다시 빌드하고 출력 창에서 `#include` 목록을 확인합니다. 각 헤더는 포함하는 헤더 아래에 들여쓰기됩니다.

## <a name="errors-involving-crt-functions"></a>CRT 함수와 관련된 오류

지난 몇 년 동안 C 런타임에서 많은 변화가 있었습니다. 함수의 보안 버전이 많이 추가되었으며 일부는 제거되었습니다. 또한이 문서의 앞부분에서 설명한 바와 같이 Microsoft의 CRT 구현은 Visual Studio 2015에서 새 이진 파일 및 관련 .lib 파일로 리팩터링 되었습니다.

오류가 CRT 함수와 관련된 경우 [Visual C++ 변경 기록 2003~2015](visual-cpp-change-history-2003-2015.md) 또는 [Visual Studio의 C++ 규칙 향상](../overview/cpp-conformance-improvements.md)을 검색하여 해당 문서에 추가 정보가 들어 있는지 확인합니다. 오류가 LNK2019, 확인할 수 없는 외부 참조인 경우 함수가 제거되지 않았는지 확인합니다. 또는 함수가 확실히 존재하고 호출 코드가 올바른 경우 프로젝트에서 `/NODEFAULTLIB`를 사용하는지 확인합니다. 그렇다면 프로젝트에서 새로운 유니버설(UCRT) 라이브러리를 사용하도록 라이브러리 목록을 업데이트해야 합니다. 자세한 내용은 라이브러리 및 종속성에 대한 위 섹션을 참조하세요.

오류가 `printf` 또는 `scanf`와 관련된 경우 stdio.h를 포함하지 않고 개인적으로 함수를 정의하지 않았는지 확인합니다. 이 경우에 개별 정의를 제거하거나 legacy\_stdio\_definitions.lib에 연결합니다. **추가 종속성** 속성에 있는 **구성 속성** > **링커** > **입력** 아래의 **속성 페이지** 대화 상자에서 이 라이브러리를 설정할 수 있습니다. Windows SDK 8.1 이전 버전에 연결하는 경우 legacy\_stdio\_definitions.lib를 추가합니다.

오류가 형식 문자열 인수와 관련된 경우 컴파일러가 표준 적용에 대해 보다 엄격하기 때문일 수 있습니다. 자세한 내용은 변경 기록을 참조하세요. 여기에 포함된 오류는 잠재적으로 보안 위험을 나타낼 수 있으므로 특히 주의하세요.

## <a name="errors-due-to-changes-in-the-c-standard"></a>C++ 표준의 변경 내용으로 인한 오류

C++ 표준 자체가 이전 버전과 항상 호환되지는 않는 방식으로 발전해 왔습니다. 이동 의미 체계, 새로운 키워드, 기타 언어 및 표준 라이브러리 기능으로 이루어진 C++11이 도입되면서 잠재적으로 컴파일러 오류와 다른 런타임 동작이 발생할 수 있습니다.

예를 들어 이전 C++ 프로그램에 iostream.h 헤더가 있을 수 있습니다. 이 헤더는 C++의 초기에 사용이 중단되었으며 결국 Visual Studio에서 완전히 제거되었습니다. 이 경우에는를 사용 하 여 \<iostream> 코드를 다시 작성 해야 합니다. 자세한 내용은 [이전 iostreams 코드 업데이트](porting-guide-spy-increment.md#updating_iostreams_code)를 참조하세요.

### <a name="c4838-narrowing-conversion-warning"></a>C4838: 축소 변환 경고

이제 C++ 표준에서 부호 없는 정수 계열 값에서 부호 있는 정수 계열 값으로의 변환을 축소 변환으로 간주하도록 지정합니다. Visual Studio 2015 이전에는 컴파일러에서 이 경고가 발생하지 않았습니다. 각 항목을 검사하여 범위를 좁히는 것이 코드의 정확성에 영향을 주지 않는지 확인합니다.

## <a name="warnings-to-use-secure-crt-functions"></a>보안 CRT 함수를 사용하도록 경고

지난 몇 년 동안 C 런타임 함수의 보안 버전이 도입되었습니다. 오래된 비보안 버전도 계속 사용할 수 있지만 보안 버전을 사용하도록 코드를 변경하는 것이 좋습니다. 컴파일러에서 비보안 버전의 사용에 대한 경고가 발생합니다. 이러한 경고를 사용하지 않거나 무시하도록 선택할 수 있습니다. 솔루션의 모든 프로젝트에 대해 경고를 사용 하지 않도록 설정 하려면 속성 관리자 **보기** 를 열고  >  경고를 사용 하지 않을 프로젝트를 모두 선택한 다음 선택한 항목을 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다. **구성 속성** > **C/C++** > **고급** 아래의 **속성 페이지** 대화 상자에서 **특정 경고 사용 안 함** 을 선택합니다. 드롭다운 화살표를 클릭한 다음, **편집** 을 클릭합니다. 텍스트 상자에 4996을 입력합니다. (' C ' 접두사는 포함 하지 마세요.) 자세한 내용은 [보안 CRT를 사용 하도록 포팅](porting-guide-spy-increment.md#porting_to_secure_crt)을 참조 하세요.

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>Windows API의 변경 내용 또는 오래된 SDK로 인한 오류

지난 몇 년 동안 Windows API와 데이터 형식이 추가되었으며, 때로는 변경되거나 제거되었습니다. 또한 핵심 운영 체제에 속하지 않는 다른 SDK가 등장하고 사라졌습니다. 따라서 오래된 프로그램에는 더 이상 존재하지 않는 API 호출이 있을 수 있습니다. 또한 더 이상 지원되지 않는 다른 Microsoft SDK의 API 호출이 있는 경우도 있습니다. Windows API 또는 이전 Microsoft SDK의 API와 관련된 오류가 표시되는 경우 API가 제거되었거나 최신 보안 함수로 대체되었을 수 있습니다.

현재 API 집합과 특정 Windows API에 대해 지원 되는 최소 운영 체제에 대 한 자세한 내용은 [데스크톱 Windows 응용 프로그램용 Api 인덱스](/windows/win32/apiindex/api-index-portal) 를 참조 하 고 해당 api로 이동 합니다.

### <a name="windows-version"></a>Windows 버전

Windows API를 직접 또는 간접적으로 사용하는 프로그램을 업그레이드하는 경우 지원할 최소 Windows 버전을 결정해야 합니다. 대부분의 경우 Windows 7을 선택하는 것이 좋습니다. 자세한 내용은 [헤더 파일 문제](porting-guide-spy-increment.md#header_file_problems)를 참조하세요. `WINVER` 매크로는 프로그램이 실행되도록 설계된 가장 오래된 Windows 버전을 정의합니다. MFC 프로그램이 WINVER을 0x0501(Windows XP)로 설정하는 경우 MFC에서 XP를 더 이상 지원하기 않으므로 컴파일러 자체에 XP 모드가 있어도 경고가 발생합니다.

자세한 내용은 [대상 Windows 버전 업데이트](porting-guide-spy-increment.md#updating_winver) 및 [더 오래된 헤더 파일](porting-guide-spy-increment.md#outdated_header_files)을 참조하세요.

## <a name="atl--mfc"></a>ATL/MFC

ATL 및 MFC는 비교적 안정된 API이지만 때때로 변경됩니다. 자세한 내용은 [Visual C++ 변경 기록 2003~2015](visual-cpp-change-history-2003-2015.md), [Visual Studio의 Visual C++에 대한 새로운 기능](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) 및 [Visual Studio의 C++ 규칙 향상](../overview/cpp-conformance-improvements.md)을 참조하세요.

### <a name="lnk-2005-_dllmain12-already-defined-in-msvcrtdlib"></a>LNK 2005 _DllMain@12가 MSVCRTD.lib에 이미 정의되어 있습니다.

이 오류는 MFC 애플리케이션에서 발생할 수 있습니다. CRT 라이브러리와 MFC 라이브러리 간의 순서 지정 문제를 나타냅니다. MFC가 new 및 delete 연산자를 제공하도록 먼저 연결되어야 합니다. 오류를 해결하려면 `/NODEFAULTLIB` 스위치를 사용하여 기본 라이브러리 MSVCRTD.lib 및 mfcs140d.lib를 무시합니다. 그런 다음 동일한 라이브러리를 추가 종속성으로 추가합니다.

## <a name="32-vs-64-bit"></a>32비트 및 64비트

원래 코드가 32비트 시스템용으로 컴파일된 경우 새로운 32비트 앱 대신(또는 추가로) 64비트 버전을 만들 수 있습니다. 일반적으로 먼저 32비트 모드로 프로그램을 컴파일한 다음 64비트를 시도해야 합니다. 64비트용 컴파일 작업은 간단하지만, 경우에 따라 32비트 빌드에서 숨겨진 버그가 나타날 수 있습니다.

또한 printf 및 scanf 함수의 포인터 크기, 시간 및 크기 값, 형식 지정자와 관련된 가능한 컴파일 시간 및 런타임 문제에 주의해야 합니다. 자세한 내용은 [64비트용 Visual C++ 구성(x64 대상)](../build/configuring-programs-for-64-bit-visual-cpp.md) 및 [일반적인 Visual C++ 64비트 마이그레이션 문제](../build/common-visual-cpp-64-bit-migration-issues.md)를 참조하세요. 추가 마이그레이션 팁은 [64비트 Windows에 대한 프로그래밍 가이드](/windows/win32/WinProg64/programming-guide-for-64-bit-windows)를 참조하세요.

## <a name="unicode-vs-mbcsascii"></a>유니코드 및 멀티바이트 문자 집합(MBCS)/ASCII

유니코드가 표준화되기 전에는 대부분의 프로그램이 MBCS(멀티바이트 문자 집합)를 사용하여 ASCII 문자 집합에 포함되지 않은 문자를 표현했습니다. 이전 MFC 프로젝트에서는 MBCS가 기본 설정이었으며, 이러한 프로그램을 업그레이드하는 경우 대신 유니코드를 사용하라는 경고가 표시됩니다. 유니코드로 변환이 개발 비용의 가치가 없다고 결정하는 경우 경고를 사용하지 않거나 무시하도록 선택할 수 있습니다. 솔루션의 모든 프로젝트에 대해이 기능을 사용 하지 않도록 설정 하려면 속성 관리자 **보기** 를 열고  >  경고를 사용 하지 않을 프로젝트를 모두 선택한 다음 선택한 항목을 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다. **속성 페이지** 대화 상자에서 **구성 속성** > **C/C++** > **고급** 을 선택합니다. **특정 경고 사용 안 함** 속성에서 드롭다운 화살표를 열고 **편집** 을 선택 합니다. 텍스트 상자에 4996을 입력합니다. (' C ' 접두사는 포함 하지 마세요.) **확인** 을 선택 하 여 속성을 저장 한 다음 **확인** 을 선택 하 여 변경 내용을 저장 합니다.

자세한 내용은 [MBCS에서 유니코드로 포팅](porting-guide-spy-increment.md#porting_to_unicode)을 참조하세요. MBCS와 유니코드에 대 한 일반적인 내용은 Visual C++ 및 [국제화](../c-runtime-library/internationalization.md) [의 텍스트 및 문자열](../text/text-and-strings-in-visual-cpp.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[이전 버전의 Visual C++에서 프로젝트 업그레이드](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Visual Studio의 C++ 규칙 향상](../overview/cpp-conformance-improvements.md)
