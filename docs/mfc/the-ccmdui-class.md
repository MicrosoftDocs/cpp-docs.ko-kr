---
description: '자세히 알아보기: CCmdUI 클래스'
title: CCmdUI 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
ms.openlocfilehash: 5fae6d2dda948fd3720a29d502d7f050e388bceb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216134"
---
# <a name="the-ccmdui-class"></a>CCmdUI 클래스

업데이트 명령을 해당 처리기로 라우팅하는 경우 프레임 워크는 `CCmdUI` 개체 (또는 파생 클래스의 개체)에 대 한 포인터를 처리기에 전달 합니다 `CCmdUI` . 이 개체는 메뉴 항목 또는 도구 모음 단추나 명령을 생성 한 다른 사용자 인터페이스 개체를 나타냅니다. 업데이트 처리기는 `CCmdUI` 포인터를 통해 구조체의 멤버 함수를 호출 하 여 사용자 인터페이스 개체를 업데이트 합니다. 예를 들어 다음은 모두 지우기 메뉴 항목에 대 한 업데이트 처리기입니다.

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

이 처리기는 `Enable` 메뉴 항목에 대 한 액세스 권한이 있는 개체의 멤버 함수를 호출 합니다. `Enable` 항목을 사용할 수 있도록 합니다.

## <a name="see-also"></a>참고 항목

[방법: User-Interface 개체 업데이트](../mfc/how-to-update-user-interface-objects.md)
