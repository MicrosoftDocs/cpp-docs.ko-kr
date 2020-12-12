---
description: '자세한 정보: 서버: In-Place 프레임 창 구현'
title: '서버: 내부 프레임 창 구현'
ms.date: 09/09/2019
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
ms.openlocfilehash: 859a31bf107162aea6adb4d40ccf7b7b87f485b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217356"
---
# <a name="servers-implementing-in-place-frame-windows"></a>서버: 내부 프레임 창 구현

이 문서에서는 서버 애플리케이션을 만들 때 애플리케이션 마법사를 사용하지 않는 경우, 시각적인 편집 서버 애플리케이션에서 내부 프레임 창을 구현하기 위해 수행해야 하는 작업에 대해 설명합니다. 이 문서에 설명 된 절차를 수행 하는 대신 응용 프로그램 마법사에서 생성 된 응용 프로그램 또는 Visual C++ 제공 된 샘플에서 기존 내부 프레임 창 클래스를 사용할 수 있습니다.

#### <a name="to-declare-an-in-place-frame-window-class"></a>내부 frame-window 클래스를 선언하려면

1. `COleIPFrameWnd`에서 내부 frame-window 클래스를 파생합니다.

   - 클래스 헤더 파일에 DECLARE_DYNCREATE 매크로를 사용 합니다.

   - 클래스 구현 파일 (.cpp)에서 IMPLEMENT_DYNCREATE 매크로를 사용 합니다. 이렇게 하면 프레임워크가 이 클래스의 개체를 만들 수 있습니다.

1. frame-window 클래스에서 `COleResizeBar` 멤버를 선언합니다. 이 멤버는 서버 애플리케이션의 내부 크기 조정을 지원하려는 경우에 필요합니다.

   `OnCreate` [클래스 마법사](reference/mfc-class-wizard.md)를 사용 하 여 메시지 처리기를 선언 하 고 `Create` 멤버에 대해를 호출 `COleResizeBar` 합니다 (정의 된 경우).

1. 도구 모음이 있으면 frame-window 클래스에서 `CToolBar` 멤버를 선언합니다.

   서버가 내부에서 활성 상태일 때 도구 모음을 만들도록 `OnCreateControlBars` 멤버 함수를 재정의합니다. 예를 들어:

   [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]

   5단계의 코드 설명을 참조하십시오.

1. 기본 .cpp 파일에서 이 내부 frame-window 클래스에 대한 헤더 파일을 포함합니다.

1. 애플리케이션 클래스에 대한 `InitInstance`에서 문서 템플릿 개체의 `SetServerInfo` 함수를 호출하여 열기 및 내부 편집에 사용할 리소스 및 내부 프레임 창을 지정합니다.

문의 일련의 함수 호출은 서버에서 **`if`** 제공 하는 리소스에서 도구 모음을 만듭니다. 이 지점에서 도구 모음은 컨테이너의 창 계층의 일부입니다. 도구 모음이 `CToolBar`에서 파생되기 때문에 소유자를 변경하지 않는 한, 해당 메시지를 소유자 즉, 컨테이너 애플리케이션의 프레임 창으로 전달합니다. `SetOwner` 호출이 필요한 이유는 바로 이 때문입니다. 이 호출은 명령이 서버의 내부 프레임 창에 전달되는 창을 변경해서 메시지가 서버에 전달되도록 합니다. 그러면 서버가 제공된 도구 모음에서 작업에 반응할 수 있습니다.

도구 모음 비트맵 ID는 서버 애플리케이션에 정의된 다른 내부 리소스와 동일해야 합니다. 자세한 내용은 [메뉴 및 리소스: 서버 추가](../mfc/menus-and-resources-server-additions.md) 를 참조 하세요.

자세한 내용은 *클래스 라이브러리 참조* 에서 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md), [COleResizeBar](../mfc/reference/coleresizebar-class.md)및 [cdoctemplate:: SetServerInfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[서버](../mfc/servers.md)<br/>
[서버: 서버 구현](../mfc/servers-implementing-a-server.md)<br/>
[서버: 서버 문서 구현](../mfc/servers-implementing-server-documents.md)<br/>
[서버: 서버 항목](../mfc/servers-server-items.md)
