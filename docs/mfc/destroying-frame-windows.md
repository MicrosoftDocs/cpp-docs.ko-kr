---
description: '자세한 정보: 프레임 창 소멸'
title: 프레임 창 제거
ms.date: 11/04/2016
f1_keywords:
- PostNcDestroy
helpviewer_keywords:
- Default method [MFC]
- DestroyWindow method [MFC]
- frame windows [MFC], destroying
- OnNcDestroy method, and frame windows
- document frame windows [MFC], destroying
- destroying frame windows
- MFC, frame windows
- windows [MFC], destroying
- OnClose method [MFC]
- PostNcDestroy method [MFC]
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
ms.openlocfilehash: 192b1b21881f4a9f94a4fb1d6c7b18b4a91ac579
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327857"
---
# <a name="destroying-frame-windows"></a>프레임 창 제거

MFC 프레임 워크는 프레임 워크 문서와 뷰와 연결 된 창에 대 한 생성 뿐만 아니라 창 소멸을 관리 합니다. 추가 창을 만드는 경우 제거 해야 합니다.

프레임 워크에서 사용자가 프레임 창을 닫으면 창의 기본 [OnClose](reference/cwnd-class.md#onclose) 처리기는 [DestroyWindow](reference/cwnd-class.md#destroywindow)를 호출 합니다. Windows 창이 제거 될 때 호출 되는 마지막 멤버 함수는 [OnNcDestroy](reference/cwnd-class.md#onncdestroy)입니다 .이 함수는 정리를 수행 하 고 [기본](reference/cwnd-class.md#default) 멤버 함수를 호출 하 여 windows 정리를 수행 하며, 마지막으로 가상 멤버 함수 [PostNcDestroy](reference/cwnd-class.md#postncdestroy)를 호출 합니다. 의 [CFrameWnd](reference/cframewnd-class.md) 구현은 `PostNcDestroy` c + + 창 개체를 삭제 합니다. 프레임 창에는 c + + 연산자를 사용 하면 안 **`delete`** 됩니다. 대신 `DestroyWindow`를 사용하세요.

주 창이 닫히면 응용 프로그램이 닫힙니다. 저장 하지 않은 문서가 수정 된 경우 프레임 워크는 문서를 저장 해야 하는지 여부를 묻는 메시지 상자를 표시 하 고 필요한 경우 적절 한 문서가 저장 되도록 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [문서 프레임 창 만들기](creating-document-frame-windows.md)

## <a name="see-also"></a>참고 항목

[프레임 창 사용](using-frame-windows.md)
