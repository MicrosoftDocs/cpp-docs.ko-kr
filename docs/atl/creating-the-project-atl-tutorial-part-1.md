---
description: '자세히 알아보기: 프로젝트 만들기 (ATL 자습서, 1 부)'
title: 프로젝트 만들기(ATL 자습서, 1부)
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
ms.openlocfilehash: f594294b5d97222791a3f3f43c147fae9514889b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148088"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>프로젝트 만들기(ATL 자습서, 1부)

이 자습서에서는 다각형을 표시 하는 ActiveX 개체를 만드는 특성을 사용 하지 않는 ATL 프로젝트를 단계별로 안내 합니다. 개체에는 사용자가 다각형을 구성 하는 변의 수와 디스플레이를 새로 고치는 코드를 변경할 수 있는 옵션이 포함 되어 있습니다.

> [!NOTE]
> 이 자습서는 Polygon 샘플과 동일한 소스 코드를 만듭니다. 소스 코드를 수동으로 입력 하지 않으려면 [Polygon sample abstract](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/Polygon)에서 다운로드할 수 있습니다. 그런 다음 자습서를 통해 작업할 때 Polygon 소스 코드를 참조 하거나,이를 사용 하 여 프로젝트에서 오류를 확인할 수 있습니다.
> 컴파일하려면 *.pch* (Visual Studio 2017 및 이전 버전에서 *stdafx.h* )를 열고 다음을 바꿉니다.
>
> ```
> #ifndef WINVER
> #define WINVER 0x0400
> #endif
> ```
>
> 다음과 같이 바꿉니다.
>
> ```
> #ifndef WINVER
> #define WINVER 0x0500
> #define _WIN32_WINNT 0x0500
> #endif
> ```
>
> 컴파일러는 `regsvr32` 제대로 종료 되지 않는 것을 여전히 확인할 수 있지만, 컨트롤의 DLL을 빌드하고 사용할 수 있어야 합니다.

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>ATL 프로젝트 마법사를 사용 하 여 초기 ATL 프로젝트를 만들려면

1. Visual Studio 2017 이전 버전: **파일**  >  **새로 만들기**  >  **프로젝트**. **Visual C++** 탭을 열고 **MFC/ATL** 을 선택 합니다. **ATL 프로젝트** 를 선택 합니다.

   Visual Studio 2019: **파일**  >  **새로 만들기**  >  **프로젝트** 를 선택 하 고 검색 상자에 "atl"을 입력 한 다음 **atl 프로젝트** 를 선택 합니다.

1. 프로젝트 이름으로 *Polygon* 을 입력 합니다.

    소스 코드의 위치는 일반적으로 \Users \\ \<username> \source\repos이 고 새 폴더는 자동으로 만들어집니다.

1. Visual Studio 2019에서 기본값을 그대로 적용 하 고 **확인** 을 클릭 합니다.
   Visual Studio 2017에서 **확인** 을 클릭 하 여 **ATL 프로젝트** 마법사를 엽니다. **응용 프로그램 설정** 을 클릭 하 여 사용할 수 있는 옵션을 확인 합니다. 이 프로젝트는 컨트롤을 만들지만 컨트롤이 in-process 서버 여야 하므로 **응용 프로그램 유형을** DLL로 그대로 둡니다. **확인** 을 클릭합니다.

Visual Studio에서 여러 파일을 생성 하 여 프로젝트를 만듭니다. 이러한 파일은 개체를 확장 하 여 **솔루션 탐색기** 에서 볼 수 있습니다 `Polygon` . 파일은 아래에 나열 되어 있습니다.

::: moniker range="<=msvc-150"

|파일|설명|
|----------|-----------------|
|Polygon .cpp|에는,, `DllMain` `DllCanUnloadNow` `DllGetClassObject` , 및의 `DllRegisterServer` 구현이 포함 되어 있습니다 `DllUnregisterServer` . 프로젝트의 ATL 개체 목록 인 개체 맵도 포함 합니다. 처음에는 비어 있습니다.|
|Polygon .def|이 모듈 정의 파일은 DLL에 필요한 내보내기에 대 한 정보를 링커에 제공 합니다.|
|Polygon .idl|인터페이스 정의 언어 파일은 개체에 특정 한 인터페이스를 설명 합니다.|
|Polygon. rgs|이 레지스트리 스크립트는 프로그램의 DLL을 등록 하는 데 필요한 정보를 포함 합니다.|
|Polygon .rc|처음에는 버전 정보와 프로젝트 이름을 포함 하는 문자열을 포함 하는 리소스 파일입니다.|
|Resource.h|리소스 파일용 헤더 파일.|
|Polygonps|이 모듈 정의 파일은 프록시 및 아파트 간 호출을 지 원하는 스텁 코드에서 필요한 내보내기에 대 한 정보를 링커에 제공 합니다.|
|stdafx.cpp|Stdafx.h를 받을 파일입니다. `#include` |
|stdafx.h|`#include`ATL 헤더 파일을 미리 컴파일하는 파일입니다.|

::: moniker-end

::: moniker range=">=msvc-160"

|파일|설명|
|----------|-----------------|
|Polygon .cpp|에는,, `DllMain` `DllCanUnloadNow` `DllGetClassObject` , 및의 `DllRegisterServer` 구현이 포함 되어 있습니다 `DllUnregisterServer` . 프로젝트의 ATL 개체 목록 인 개체 맵도 포함 합니다. 처음에는 비어 있습니다.|
|Polygon .def|이 모듈 정의 파일은 DLL에 필요한 내보내기에 대 한 정보를 링커에 제공 합니다.|
|Polygon .idl|인터페이스 정의 언어 파일은 개체에 특정 한 인터페이스를 설명 합니다.|
|Polygon. rgs|이 레지스트리 스크립트는 프로그램의 DLL을 등록 하는 데 필요한 정보를 포함 합니다.|
|Polygon .rc|처음에는 버전 정보와 프로젝트 이름을 포함 하는 문자열을 포함 하는 리소스 파일입니다.|
|Resource.h|리소스 파일용 헤더 파일.|
|Polygonps|이 모듈 정의 파일은 프록시 및 아파트 간 호출을 지 원하는 스텁 코드에서 필요한 내보내기에 대 한 정보를 링커에 제공 합니다.|
|.pch .cpp|Pch를 받을 파일입니다 `#include` *.*|
|.pch. h|`#include`ATL 헤더 파일을 미리 컴파일하는 파일입니다.|

::: moniker-end

1. **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 `Polygon` 합니다.

1. 바로 가기 메뉴에서 **속성** 을 클릭 합니다.

1. **링커** 를 클릭 합니다. **UserRedirection** 옵션을 **예** 로 변경 합니다.

1. **확인** 을 클릭합니다.

다음 단계에서는 프로젝트에 컨트롤을 추가 합니다.

[2 단계에서](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>참고 항목

[자습서](../atl/active-template-library-atl-tutorial.md)
