---
description: '자세한 정보: 라이브러리 및 구성 요소 사용'
title: C++ 프로젝트에서 라이브러리 및 구성 요소 사용
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: a8933afc1d3d9257e4a8b1d80a39c5fa15a9d438
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163264"
---
# <a name="consuming-libraries-and-components"></a>라이브러리 및 구성 요소 사용

C++ 프로젝트는 함수를 호출하거나 정적 라이브러리(.lib 파일), DLL, Windows 런타임 구성 요소, COM 구성 요소 또는 .NET 어셈블리와 같은 이진 파일의 데이터에 액세스해야 하는 경우가 종종 있습니다. 이러한 경우 빌드 시 이러한 이진 파일을 찾을 수 있도록 프로젝트를 구성해야 합니다. 특정 단계는 프로젝트의 형식, 이진 파일의 형식, 이진 파일이 프로젝트와 동일한 솔루션에 빌드되었는지 여부에 따라 달라집니다.

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>vcpkg를 통해 다운로드된 라이브러리 사용

**vcpkg** 패키지 관리자를 사용하여 다운로드한 라이브러리를 사용하려면 아래 지침을 무시해도 됩니다. [vcpkg: Windows, Linux 및 MacOS용 C++ 패키지 관리자](vcpkg.md#integrate-with-visual-studio-windows)에서 자세한 내용을 확인할 수 있습니다.

## <a name="consuming-static-libraries"></a>정적 라이브러리 사용

정적 라이브러리 프로젝트가 동일한 솔루션에서 빌드되는 경우:

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>따옴표를 사용하여 정적 라이브러리의 헤더 파일을 포함합니다. 일반적인 솔루션에서는 경로가 `../<library project name>`으로 시작됩니다. IntelliSense를 통해 찾을 수 있습니다.
2. 정적 라이브러리 프로젝트에 참조를 추가합니다. **솔루션 탐색기** 의 애플리케이션 프로젝트 노드에서 **참조** 를 마우스 오른쪽 단추로 클릭하고 **참조 추가** 를 선택합니다.

정적 라이브러리가 솔루션에 포함되지 않은 경우:

1. **솔루션 탐색기** 에서 애플리케이션 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택합니다.
2. **VC++ 디렉터리** 속성 페이지에서 .lib 파일이 **라이브러리 경로** 에 있는 디렉터리에 경로를 추가하고 **포함 디렉터리** 에 라이브러리 헤더 파일에 대한 경로를 추가합니다.  
3. **링커 > 입력** 속성 페이지에서 **추가 종속성** 에 .lib 파일의 이름을 추가합니다.

## <a name="dynamic-link-libraries"></a>동적 연결 라이브러리

애플리케이션과 동일한 솔루션의 일부로 DLL을 빌드하는 경우에는 정적 라이브러리의 경우와 동일한 단계를 따르세요.

DLL이 애플리케이션 솔루션에 포함되어 있지 않으면 DLL 파일, 내보낸 함수 및 클래스의 프로토타입이 포함된 헤더, 필요한 연결 정보를 제공하는 .lib 파일이 필요합니다.

1. DLL을 프로젝트의 출력 폴더 또는 DLL의 표준 Windows 검색 경로에 있는 다른 폴더에 복사합니다. [동적 연결 라이브러리 검색 순서](/windows/win32/dlls/dynamic-link-library-search-order)를 참조하세요.
2. 정적 라이브러리에 대해 1-3단계를 수행하여 헤더 및 .lib 파일의 경로를 제공합니다.

## <a name="com-objects"></a>COM 개체

네이티브 C++ 애플리케이션에서 COM 개체를 사용해야 하고 이 개체가 *등록된* 경우에는 CoCreateInstance를 호출하여 개체의 CLSID에 전달하기만 하면 됩니다. 시스템이 Windows 레지스트리에서 이를 검색하여 로드합니다. C++/CLI 프로젝트는 동일한 방식으로 COM 개체를 사용하거나, **참조 추가 > COM** 목록에서 이 개체에 참조를 추가하고 [런타임 호출 가능 래퍼](/dotnet/framework/interop/runtime-callable-wrapper)를 통해 COM 개체를 사용할 수 있습니다.

## <a name="net-assemblies-and-windows-runtime-components"></a>.NET 어셈블리 및 Windows 런타임 구성 요소

UWP 또는 C++/CLI 프로젝트에서 어셈블리 또는 구성 요소에 *참조* 를 추가하여 .NET 어셈블리 또는 Windows 런타임 구성 요소를 사용합니다. UWP 또는 C++/CLI 프로젝트의 **참조** 노드에서는 일반적으로 사용되는 구성 요소에 대한 참조를 볼 수 있습니다. **솔루션 탐색기** 에서 **참조** 노드를 마우스 오른쪽 단추로 클릭하여 **참조 관리자** 를 표시하고 시스템에 알려진 추가 구성 요소를 찾습니다. **찾아보기** 단추를 클릭하여 사용자 지정 구성 요소가 있는 폴더로 이동합니다. .NET 어셈블리 및 Windows 런타임 구성 요소에는 기본 제공 형식 정보가 포함되어 있으므로 **개체 브라우저에서 보기** 를 마우스 오른쪽 단추로 클릭해 선택하여 해당 메서드 및 클래스를 볼 수 있습니다.

## <a name="reference-properties"></a>참조 속성

각 종류의 참조에는 속성이 있습니다. 속성은 솔루션 탐색기에서 참조를 선택하고 **Alt+Enter** 를 누르거나 마우스 오른쪽 단추를 클릭하고 **속성** 을 선택하여 볼 수 있습니다. 일부 속성은 읽기 전용이며 일부는 수정할 수 있습니다. 그러나 일반적으로 이러한 속성은 수정할 필요가 없습니다.

### <a name="activex-reference-properties"></a>ActiveX 참조 속성

ActiveX 참조 속성은 COM 구성 요소에 대한 참조에만 사용할 수 있습니다. **참조** 창에서 COM 구성 요소를 선택한 경우에만 이러한 속성이 표시됩니다. 이러한 속성은 수정할 수 없습니다.

- **컨트롤 전체 경로**

   참조된 컨트롤의 디렉터리 경로를 표시합니다.

- **컨트롤 GUID**

   ActiveX 컨트롤에 대한 GUID를 표시합니다.

- **컨트롤 버전**

   참조된 ActiveX 컨트롤의 버전을 표시합니다.

- **형식 라이브러리 이름**

   참조된 형식 라이브러리의 이름을 표시합니다.

- **래퍼 도구**

   참조된 COM 라이브러리 또는 ActiveX 컨트롤에서 interop 어셈블리를 빌드하는 데 사용되는 도구를 표시합니다.

### <a name="assembly-reference-properties-ccli"></a>어셈블리 참조 속성(C++/CLI)

어셈블리 참조 속성은 C++/CLI 프로젝트의 .NET Framework 어셈블리에 대한 참조에만 사용할 수 있습니다. 이러한 속성은 **참조** 창에서 .NET Framework 어셈블리를 선택한 경우에만 표시됩니다. 이러한 속성은 수정할 수 없습니다.

- **상대 경로**

   참조된 어셈블리에 대한 프로젝트 디렉터리의 상대 경로를 표시합니다.

### <a name="build-properties"></a>빌드 속성

다음 속성은 다양한 종류의 참조에서 사용할 수 있습니다. 이러한 속성을 사용하면 참조로 빌드하는 방법을 지정할 수 있습니다.

- **로컬 복사**

   빌드 중 대상 위치에 대해 참조되는 어셈블리를 자동으로 복사할지 지정합니다.

- **로컬 위성 어셈블리 복사(C++/CLI)**

   참조된 어셈블리의 위성 어셈블리를 빌드 중에 대상 위치에 자동으로 복사할지 지정합니다. **로컬 복사** 가 **`true`** 인 경우에만 사용됩니다.

- **참조 어셈블리 출력**

   이 어셈블리가 빌드 프로세스에서 사용되도록 지정합니다. **`true`** 이면 빌드 중 어셈블리가 컴파일러 명령줄에서 사용됩니다.

### <a name="project-to-project-reference-properties"></a>프로젝트 간 참조 속성

다음 속성은 **참조** 창에서 선택한 프로젝트에서 동일한 솔루션의 다른 프로젝트로의 *프로젝트 간 참조* 를 정의합니다. 자세한 내용은 [프로젝트의 참조 관리](/visualstudio/ide/managing-references-in-a-project)를 참조하세요.

- **라이브러리 종속성 링크**

   이 속성이 **True** 이면 독립 프로젝트에서 생성한 .lib 파일인 종속 프로젝트에 프로젝트 시스템이 연결됩니다. 일반적으로 **True** 를 지정합니다.

- **프로젝트 식별자**

   독립 프로젝트를 고유하게 식별합니다. 속성 값은 수정할 수 없는 내부 시스템 GUID입니다.

- **라이브러리 종속성 입력 사용**

   이 속성이 **False** 이면 프로젝트 시스템이 종속 프로젝트에서 생성한 라이브러리에 대한 .obj 파일인 종속 프로젝트에 연결되지 않습니다. 따라서 이 값은 증분 링크를 해제합니다. 일반적으로 독립 프로젝트가 많은 경우 애플리케이션을 빌드하는 데 시간이 오래 걸릴 수 있으므로 **False** 를 지정합니다.

### <a name="read-only-reference-properties-com--net"></a>읽기 전용 참조 속성(COM 및 .NET)

다음 속성은 COM 및 .NET 어셈블리 참조에 있으며 수정할 수 없습니다.

- **어셈블리 이름**

   참조된 어셈블리에 대한 어셈블리 이름을 표시합니다.

- **문화권**.

   선택한 참조의 문화권을 표시합니다.

- **설명**

   선택한 참조에 대한 설명을 표시합니다.

- **전체 경로**

   참조된 어셈블리의 디렉터리 경로를 표시합니다.

- **ID**

   .NET Framework 어셈블리의 경우 전체 경로를 표시합니다. COM 구성 요소의 경우 GUID를 표시합니다.

- **레이블**

   참조의 레이블을 표시합니다.

- **이름**

   참조 이름을 표시합니다.

- **공개 키 토큰**

   참조된 어셈블리를 식별하는 데 사용되는 공개 키 토큰을 표시합니다.

- **강력한 이름**

   참조된 어셈블리에 강력한 이름이 있는 경우 **`true`** 입니다. 강력한 이름이 지정된 어셈블리의 버전은 고유합니다.

- **Version**

   참조된 어셈블리의 버전을 표시합니다.

## <a name="see-also"></a>참조

[C++ 프로젝트 속성 페이지 참조](reference/property-pages-visual-cpp.md)<br>
[Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](working-with-project-properties.md)
