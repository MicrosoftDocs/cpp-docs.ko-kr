---
description: '자세한 정보: DHTML 컨트롤에 대 한 ATL 지원'
title: DHTML 컨트롤에 대한 ATL 지원
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
ms.openlocfilehash: 7527527bc5574470fd361bae2375c25ce9345f3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148592"
---
# <a name="atl-support-for-dhtml-controls"></a>DHTML 컨트롤에 대한 ATL 지원

ATL을 사용 하면 DHTML (Dynamic HTML) 기능을 사용 하 여 컨트롤을 만들 수 있습니다. ATL DHTML 컨트롤:

- WebBrowser 컨트롤을 호스팅합니다.

- HTML을 사용 하 여 DHTML 컨트롤의 UI (사용자 인터페이스)를 지정 합니다.

- [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\))인터페이스를 통해 WebBrowser 개체 및 해당 메서드에 액세스 합니다.

- C + + 코드와 HTML 간의 통신을 관리 합니다.

Dhtml 컨트롤은 추가 디스패치 인터페이스를 포함 하는 것을 제외 하 고 다른 ATL 컨트롤과 비슷합니다. 기본 DHTML 프로젝트에서 제공 하는 인터페이스에 대 한 그림은 [Dhtml 컨트롤 프로젝트의 요소 식별](../atl/identifying-the-elements-of-the-dhtml-control-project.md) 그림을 참조 하세요.

웹 브라우저나 ActiveX 컨트롤 테스트 컨테이너와 같은 다른 컨테이너에서 ATL DHTML 컨트롤을 볼 수 있습니다.

## <a name="in-this-section"></a>섹션 내용

[DHTML 컨트롤 프로젝트의 요소 식별](../atl/identifying-the-elements-of-the-dhtml-control-project.md)<br/>
DHTML 컨트롤 프로젝트의 요소에 대해 설명 합니다.

[DHTML에서 c + + 코드 호출](../atl/calling-cpp-code-from-dhtml.md)<br/>
DHTML 컨트롤에서 c + + 코드를 호출 하는 예제를 제공 합니다.

[ATL DHTML 컨트롤 만들기](../atl/creating-an-atl-dhtml-control.md)<br/>
DHTML 컨트롤을 만드는 단계를 나열 합니다.

[ATL DHTML 컨트롤 테스트](../atl/testing-the-atl-dhtml-control.md)<br/>
초기 DHTML 컨트롤 프로젝트를 빌드하고 테스트 하는 방법을 보여 줍니다.

[ATL DHTML 컨트롤 수정](../atl/modifying-the-atl-dhtml-control.md)<br/>
컨트롤에 일부 기능을 추가 하는 방법을 보여 줍니다.

[변경 된 ATL DHTML 컨트롤 테스트](../atl/testing-the-modified-atl-dhtml-control.md)<br/>
컨트롤의 추가 된 기능을 빌드 및 테스트 하는 방법을 보여 줍니다.

## <a name="related-sections"></a>관련 단원

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
액티브 템플릿 라이브러리를 사용하여 프로그래밍하는 방법에 대한 개념 항목의 링크를 제공합니다.
