---
title: MFC 및 ATL
ms.date: 01/24/2018
ms.assetid: 31b1a3a8-4154-4c4a-af10-fafc23ecdc5c
ms.openlocfilehash: 2d986c3237a6fa58cfcebef29939dbf6b1c316ae
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706632"
---
# <a name="mfc-and-atl"></a>MFC 및 ATL

MFC(Microsoft Foundation Class)는 Win32를 통해 C++ 개체 지향 래퍼를 제공하여 네이티브 데스크톱 애플리케이션을 신속하게 개발할 수 있습니다. ATL(액티브 템플릿 라이브러리)은 COM 개발을 간단하게 하는 래퍼 라이브러리이며 ActiveX 컨트롤을 만드는 데 광범위하게 사용됩니다.

Visual Studio Community Edition 이상을 사용하여 MFC 또는 ATL 프로그램을 만들 수 있습니다. Express 버전은 MFC 또는 ATL을 지원하지 않습니다.

Visual Studio 2015에서 Visual C++는 선택적 구성 요소이며 MFC와 ATL 구성 요소는 Visual C++ 아래의 선택적 하위 구성 요소입니다. Visual Studio를 처음 설치할 때 이러한 구성 요소를 선택하지 않으면 처음으로 MFC 또는 ATL 프로젝트를 만들거나 열려고 할 때 설치하라는 메시지가 표시됩니다.

Visual Studio 2017 및 이후 버전에서 MFC 및 ATL은 Visual Studio 설치 관리자 프로그램의 **C++를 이용한 데스크톱 개발** 워크로드의 선택적 하위 구성요소입니다. MFC나 ATL을 조합하지 않고 ATL 지원을 설치할 수 있습니다(MFC는 ATL에 의존적임). 워크 로드 및 구성 요소에 대 한 자세한 내용은 참조 하세요. [Visual Studio 설치](/visualstudio/install/install-visual-studio)합니다.

## <a name="related-articles"></a>관련 문서

|제목|설명|
|-----------|-----------------|
|[MFC 데스크톱 응용 프로그램](../mfc/mfc-desktop-applications.md)|Microsoft Foundation Class는 Win32를 통해 경량 개체 지향 래퍼를 제공하여 C++에서 GUI 응용 프로그램을 신속하게 개발할 수 있도록 합니다.|
|[ATL COM 데스크톱 구성 요소](../atl/atl-com-desktop-components.md)|ATL은 COM 개체 생성을 단순화하기 위한 클래스 템플릿 및 기타 사용 구문을 제공합니다.|
|[ATL/MFC 공유 클래스](../atl-mfc-shared/atl-mfc-shared-classes.md)|MFC와 ATL에서 공유하는 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) 및 기타 클래스에 대한 참조입니다.|
|[리소스 파일 작업](../windows/working-with-resource-files.md)|리소스 편집기를 사용하면 문자열, 이미지 및 대화 상자와 같은 UI 리소스를 편집할 수 있습니다.|
|[Visual Studio의 C++](../overview/visual-cpp-in-visual-studio.md)|MSDN 라이브러리의 모든 C++ 콘텐츠에 대한 부모 항목입니다.|