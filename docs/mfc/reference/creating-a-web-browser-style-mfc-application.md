---
description: '자세한 정보: MFC 응용 프로그램 웹 Browser-Style 만들기'
title: 웹 브라우저 스타일 MFC 애플리케이션 만들기
ms.date: 06/25/2018
f1_keywords:
- vc.appwiz.mfcweb.project
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
ms.openlocfilehash: 0ee8250be20b53979c2a3e059d83237389091e72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301284"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>웹 브라우저 스타일 MFC 애플리케이션 만들기

웹 브라우저 스타일 응용 프로그램은 인터넷 (예: HTML 또는 액티브 문서) 또는 인트라넷, 로컬 파일 시스템 및 네트워크의 폴더에 있는 정보에 액세스할 수 있습니다. [CHtmlView](../../mfc/reference/chtmlview-class.md)에서 응용 프로그램의 뷰 클래스를 파생 시키면 WebBrowser 컨트롤을 사용 하 여 뷰를 제공 하 여 응용 프로그램을 웹 브라우저로 만들 수 있습니다.

## <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>MFC 문서/뷰 아키텍처에 따라 웹 브라우저 응용 프로그램을 만들려면

1. [MFC 응용 프로그램 만들기](../../mfc/reference/creating-an-mfc-application.md)의 지침을 따릅니다.

1. MFC 응용 프로그램 마법사 [응용 프로그램 유형](../../mfc/reference/application-type-mfc-application-wizard.md) 페이지에서 **문서/뷰 아키텍처** 상자가 선택 되어 있는지 확인 합니다. **단일 문서** 또는 **여러 문서** 중 하나를 선택할 수 있지만 **대화 상자 기반** 은 선택할 수 없습니다.

1. [생성 된 클래스 검토](../../mfc/reference/generated-classes-mfc-application-wizard.md) 페이지에서 **기본 클래스** 드롭다운 메뉴를 사용 하 여를 선택 `CHtmlView` 합니다.

1. 기초 응용 프로그램에 기본으로 사용할 다른 옵션을 선택 합니다.

1. **Finish** 를 클릭합니다.

WebBrowser 컨트롤은 하이퍼링크 및 URL (Uniform Resource Locator) 탐색을 통한 웹 검색을 지원 합니다. 컨트롤은 사용자가 이전에 검색 한 사이트, 폴더 및 문서를 앞뒤로 탐색할 수 있도록 하는 기록 목록을 유지 관리 합니다. 컨트롤은 탐색, 하이퍼링크, 기록 목록, 즐겨찾기 및 보안을 직접 처리 합니다. 응용 프로그램은 WebBrowser 컨트롤을 활성 문서 컨테이너로 사용 하 여 활성 문서를 호스트할 수 있습니다. 따라서 Microsoft Excel 스프레드시트 또는 Word 문서와 같은 서식 있는 문서를 WebBrowser 컨트롤 내에서 대신 열고 편집할 수 있습니다. WebBrowser 컨트롤은 ActiveX 컨트롤을 호스팅할 수 있는 ActiveX 컨트롤 컨테이너 이기도 합니다.

> [!NOTE]
> WebBrowser ActiveX 컨트롤 (및 따라서 `CHtmlView` )은 Internet Explorer 4.0 이상이 설치 된 Windows 버전에서 실행 되는 응용 프로그램 에서만 사용할 수 있습니다.

는 `CHtmlView` 단순히 Microsoft 웹 브라우저 컨트롤을 구현 하기 때문에 다른 [CView](../../mfc/reference/cview-class.md)파생 클래스와는 인쇄를 지원 하지 않습니다. 대신 WebBrowser 컨트롤은 프린터 사용자 인터페이스 및 인쇄를 구현 합니다. 따라서에서는 `CHtmlView` 인쇄 미리 보기를 지원 하지 않으며, 다른 MFC 응용 프로그램에서 사용할 수 있는 [cview:: onprepareprinting](../../mfc/reference/cview-class.md#onprepareprinting), [Cview:: Onprepareprinting](../../mfc/reference/cview-class.md#onbeginprinting)및 [cview:: OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)와 같은 다른 인쇄 지원 기능을 프레임 워크에서 제공 하지 않습니다.

`CHtmlView` 웹 브라우저 컨트롤에 대 한 래퍼 역할을 하 여 응용 프로그램에 웹 또는 HTML 페이지에 대 한 뷰를 제공 합니다. 이 마법사는 Microsoft Visual C++ 웹 사이트에 대 한 탐색 링크를 제공 하 여 뷰 클래스에 [Oninitialupdate](../../mfc/reference/cview-class.md#oninitialupdate) 함수에 대 한 재정의를 만듭니다.

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.docs.microsoft.com/"),
        NULL,
        NULL);
}
```

이 사이트를 자체의 하나로 바꾸거나 [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) 멤버 함수를 사용 하 여 프로젝트의 리소스 스크립트에 있는 HTML 페이지를 뷰의 기본 콘텐츠로 열 수 있습니다. 예를 들어:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    LoadFromResource(IDR_HTML1);
}
```

## <a name="see-also"></a>참고 항목

[MFC 샘플 MFCIE](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet)<br/>
[MFC 응용 프로그램 마법사](../../mfc/reference/mfc-application-wizard.md)<br/>
[컴파일러 설정 및 빌드 속성](../../build/working-with-project-properties.md)<br/>
[속성 페이지](../../build/reference/property-pages-visual-cpp.md)<br/>
[컴파일러 설정 및 빌드 속성](../../build/working-with-project-properties.md)
