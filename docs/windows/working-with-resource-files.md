---
description: '자세히 알아보기: 리소스 파일 작업'
title: 리소스 파일에 대한 작업(C++)
ms.date: 02/14/2019
helpviewer_keywords:
- resources [C++], about resources
- resources [C++], about resource files
- resource files [C++], about resource files
ms.assetid: 2699a539-b369-4b78-80f0-df03eb7b6780
ms.openlocfilehash: c8e1a891839ee19201a98f9beb5e538e24c1d3f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135800"
---
# <a name="working-with-resource-files"></a>리소스 파일에 대한 작업

> [!WARNING]
> 이 섹션의 내용은 C++로 작성된 Windows 데스크톱 애플리케이션에 적용됩니다.
>
> C + +로 작성 된 유니버설 Windows 플랫폼 앱의 리소스에 대 한 자세한 내용은 [앱 리소스 정의](/windows/uwp/app-resources/)또는 c + +/cli (관리) 프로젝트에 리소스 추가를 참조 하세요. .NET Framework 개발자 가이드에서 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 를 참조 하세요.

리소스는 다음과 같은 다양 한 요소로 구성 될 수 있습니다.

- 비트맵, 아이콘 또는 커서와 같은 정보를 사용자에 게 제공 하는 인터페이스 요소입니다.
- 데이터 및 응용 프로그램 요구 사항을 포함 하는 사용자 지정 리소스.
- 설치 Api에서 사용 하는 버전 리소스입니다.
- 메뉴 및 대화 상자 리소스

프로젝트에 새 리소스를 추가하고 적절한 리소스 편집기를 사용하여 이러한 리소스를 수정할 수 있습니다. 대부분의 Visual C++ 마법사에서는 프로젝트에 대해 .rc 파일을 자동으로 생성합니다.

> [!NOTE]
> Express 버전에서는 **리소스 편집기** 와 **리소스 뷰** 사용할 수 없습니다.

관리 되는 프로젝트에 리소스 파일을 수동으로 추가 하려면 [데스크톱 앱에 대 한 리소스 파일 만들기](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)를 참조 하세요. 이 문서에는 리소스 액세스, 정적 리소스 표시, 속성에 리소스 문자열 할당 등의 방법이 포함 되어 있습니다.

관리 되는 앱에서 리소스를 세계화 및 지역화 하려면 [.NET Framework 응용 프로그램 전역화 및 지역화](/dotnet/standard/globalization-localization/index)를 참조 하세요.

## <a name="in-this-section"></a>섹션 내용

[리소스 파일](../windows/resource-files-visual-studio.md)<br/>
리소스 파일 및 Windows 데스크톱 응용 프로그램에서 리소스 파일을 사용 하는 방법에 대해 설명 합니다. 또한 리소스 파일 사용 방법을 설명 하는 문서에 대 한 링크도 제공 합니다.

[리소스 식별자 (기호)](../windows/symbols-resource-identifiers.md)<br/>
기호에 대해 설명하고, **리소스 기호** 대화 상자를 사용하여 프로젝트의 기호를 관리하는 방법에 대한 정보를 제공합니다.

[리소스 편집기](../windows/resource-editors.md)<br/>
Visual Studio에서 제공 하는 리소스 편집기와 각 편집기로 수정할 수 있는 리소스 형식을 설명 합니다. 또한 각 편집기를 사용 하는 방법에 대 한 자세한 정보 링크를 제공 합니다.

## <a name="related-sections"></a>관련 단원

[Visual Studio의 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
Visual C++ 설명서에 대한 링크를 제공합니다.

[의견 보내기](/visualstudio/ide/talk-to-us)<br/>
설명서 집합을 사용하고 기술 지원에 문의하고 액세스 가능성 기능을 적용하는 방법에 대한 정보를 확인할 수 있는 링크를 제공합니다.

## <a name="see-also"></a>참고 항목

[Windows 데스크톱 응용 프로그램](./desktop-applications-visual-cpp.md)<br/>
[메뉴 및 기타 리소스](/windows/win32/menurc/resources)
