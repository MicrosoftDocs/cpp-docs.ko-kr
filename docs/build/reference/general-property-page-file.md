---
title: 일반 속성 페이지(파일)
ms.date: 08/30/2019
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: 7626e161e6f59de32d426b558827c423a0bb050d
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041382"
---
# <a name="general-property-page-file"></a>일반 속성 페이지(파일)

이 항목은 Windows 프로젝트에 적용 됩니다. Windows 이외 프로젝트의 경우 [Linux C++ 속성 페이지 참조](../../linux/prop-pages-linux.md)를 참조하세요.

**솔루션 탐색기**파일 노드를 마우스 오른쪽 단추로 클릭 하면 **구성 속성** 노드 아래에 있는 **일반** 속성 페이지가 열립니다. 여기에는 다음 속성이 포함 됩니다.

- **빌드에서 제외 됨**

   파일을 현재 구성에 맞게 빌드해야 하는지 여부를 지정합니다.

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>을 참조하세요.

- **콘텐츠** (UWP 앱에만 적용 됨) 응용 프로그램 패키지에 포함할 콘텐츠를 파일에 포함할지 여부를 지정 합니다.

- **항목 유형**

   **항목 형식은** 빌드 프로세스 중에 파일을 처리 하는 데 사용 되는 도구를 지정 합니다. [Visual Studio에 알려진 확장명의 파일](/visualstudio/extensibility/visual-cpp-project-extensibility#project-items) 에는이 속성의 기본값이 있습니다. 사용자 지정 파일 형식이 있거나 알려진 파일 형식에 대 한 기본 도구를 재정의 하려는 경우 여기에서 사용자 지정 도구를 지정할 수 있습니다. 자세한 내용은 [사용자 지정 빌드 도구 지정](../specifying-custom-build-tools.md)을 참조하세요. 이 속성 페이지를 사용 하 여 파일이 빌드 프로세스의 일부가 되도록 지정할 수도 있습니다.

   다음 그림에서는 *.cpp* 파일에 대 한 속성 페이지를 보여 줍니다. 이러한 종류의 파일에 대 한 기본 **항목 형식은** **C/c + + 컴파일러** (*cl.exe*)이 고 속성 페이지는이 파일에만 적용할 수 있는 다양 한 컴파일러 설정을 노출 합니다.

   ![프로젝트 항목의 일반 속성 페이지](media/file-general-item-type.png "항목 유형 선택")

    다음 표에서는 기본 항목 유형을 나열 합니다.

    |파일 확장명|Item Type|기본 도구|
    |-|-|-|
    |.appx|XAML 응용 프로그램 정의|[앱 패키지 작성](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |. hlsl, .ca|HLSL 컴파일러|[fxc.exe](/windows/win32/direct3dtools/fxc)|
    |.h|C/c + + 헤더|[C/c + + 전처리기](../../preprocessor/c-cpp-preprocessor-reference.md)|
    |해당 없음|빌드에 참여 하지 않습니다.|해당 없음|
    |.xml, .xslt, .xsl|xml|[XML 편집기](/visualstudio/xml-tools/xml-editor)|
    |. resw,. resw|PRI 리소스 (UWP 앱)|[MakePri.exe](/windows/uwp/app-resources/compile-resources-manually-with-makepri)|
    ||미디어 (UWP)|[앱 패키지 작성](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.xsd|XML 데이터 생성기 도구|[Xsd.exe (XML 스키마 정의 도구)](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) (.Net 작업 필요) MSVC에는 포함 되지 않습니다.|
    ||매니페스트 도구|[mt.exe](/windows/win32/sbscs/mt-exe)|
    |.rc|리소스|[Windows 리소스 컴파일러 (rc.exe)](/windows/win32/menurc/resource-compiler)|
    |. appxmanifest.xml|앱 패키지 매니페스트|[앱 패키지 작성](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.obj|Object|[C/c + + 링커 (link.exe)](cl-invokes-the-linker.md)|
    |. .ttf|글꼴|해당 없음|
    |.txt|텍스트|해당 없음|
    |해당 없음|사용자 지정 빌드 도구|사용자 정의|
    |해당 없음|파일 복사|해당 없음|
    |. app.packagelayout|앱 패키지 레이아웃|[앱 패키지 작성](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.resx|컴파일러 관리 리소스|[Resgen.exe(리소스 파일 생성기)](/dotnet/framework/tools/resgen-exe-resource-file-generator)|
    |natvis|C + + 디버거 시각화 파일|[Natvis 프레임 워크](/visualstudio/debugger/create-custom-views-of-native-objects)|
    |.jpg, .bmp, .ico 등|이미지|응용 프로그램 유형을 기반으로 하는 리소스 컴파일러입니다.|
    |.cpp|C/c + + 컴파일러|cl.exe|

   프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>을 참조하세요.

**구성 속성** 노드의 **일반** 속성 페이지에 액세스 하는 방법에 대 한 자세한 내용은 [Visual Studio에서 c + + 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조 하세요.

## <a name="see-also"></a>참조

[C++ 프로젝트 속성 페이지 참조](property-pages-visual-cpp.md)
