---
description: '자세히 알아보기: 프레임 창 클래스 (Windows)'
title: 프레임 창 클래스(Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
ms.openlocfilehash: dcd7dea1fd138fbe2ebf3f82013b00cff5ff1f52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339711"
---
# <a name="frame-window-classes-windows"></a>프레임 창 클래스(Windows)

프레임 창은 응용 프로그램 또는 응용 프로그램의 일부를 프레임으로 하는 창입니다. 프레임 창에는 일반적으로 보기, 도구 모음 및 상태 표시줄과 같은 다른 창이 포함 됩니다. 의 경우 `CMDIFrameWnd` 개체를 간접적으로 포함할 수 있습니다 `CMDIChildWnd` .

[CFrameWnd](reference/cframewnd-class.md)<br/>
SDI 응용 프로그램의 주 프레임 창에 대 한 기본 클래스입니다. 또한 다른 모든 프레임 창 클래스에 대 한 기본 클래스입니다.

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
MDI 응용 프로그램의 주 프레임 창에 대 한 기본 클래스입니다.

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
MDI 응용 프로그램의 문서 프레임 창에 대 한 기본 클래스입니다.

[CMiniFrameWnd](reference/cminiframewnd-class.md)<br/>
절반 높이 프레임 창은 일반적으로 부동 도구 모음 주위에 표시 됩니다.

[클래스에서 파생하는 대신](reference/coleipframewnd-class.md)<br/>
서버 문서를 편집 하는 동안 보기에 대 한 프레임 창을 제공 합니다.

## <a name="related-class"></a>관련 클래스

클래스 `CMenu` 는 응용 프로그램의 메뉴에 액세스 하는 데 사용할 수 있는 인터페이스를 제공 합니다. 런타임에 동적으로 메뉴를 조작 하는 데 유용 합니다. 예를 들어 컨텍스트에 따라 메뉴 항목을 추가 하거나 삭제 하는 경우입니다. 메뉴는 프레임 창에서 가장 자주 사용 되지만 대화 상자 및 기타 비 자식 창 에서도 사용할 수 있습니다.

[CMenu](reference/cmenu-class.md)<br/>
`HMENU`응용 프로그램의 메뉴 모음 및 팝업 메뉴에 대 한 핸들을 캡슐화 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
