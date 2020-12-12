---
description: 자세한 내용은 Frame-Window 스타일 (c + +)을 (를) 확인 하세요.
title: 프레임 창 스타일(C++)
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
ms.openlocfilehash: 5d7b0effe4b7cea17eb0b5bd8208563ba552ba99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180345"
---
# <a name="frame-window-styles-c"></a>프레임 창 스타일(C++)

프레임 워크를 사용 하 여 가져오는 프레임 창은 대부분의 프로그램에 적합 하지만 고급 함수 [Precreatewindow](reference/cwnd-class.md#precreatewindow) 및 MFC 전역 함수 [AfxRegisterWndClass](reference/application-information-and-management.md#afxregisterwndclass)를 사용 하 여 추가 유연성을 얻을 수 있습니다. `PreCreateWindow` 는의 멤버 함수입니다 `CWnd` .

**WS_HSCROLL** 및 **WS_VSCROLL** 스타일을 주 프레임 창에 적용 하는 경우 사용자가 **MDICLIENT** 영역을 스크롤할 수 있도록 **MDICLIENT** 창에 대신 적용 됩니다.

창의 **FWS_ADDTOTITLE** 스타일 비트가 설정 되어 있으면 (기본적으로 설정 됨) 뷰는 프레임 창에 보기의 문서 이름에 따라 창의 제목 표시줄에 표시할 제목을 알려 줍니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- Mdi 자식 창이 포함 된 mdi 프레임 내의 창인 [mdi 자식 창 (MDICLIENT) 관리](managing-mdi-child-windows.md)

- [MFC에서 만든 창 스타일 변경](changing-the-styles-of-a-window-created-by-mfc.md)

- [창 스타일](reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>참고 항목

[프레임 창](frame-windows.md)
