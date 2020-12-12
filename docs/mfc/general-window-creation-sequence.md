---
description: '자세히 알아보기: 일반 창 만들기 시퀀스'
title: 일반 창 만들기 시퀀스
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: 78a27114ebe3ac309ea8afdc6e04df65f1df1df8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189264"
---
# <a name="general-window-creation-sequence"></a>일반 창 만들기 시퀀스

자식 창과 같은 사용자 고유의 창을 만들 때 프레임 워크는 [문서/뷰 만들기](document-view-creation.md)에 설명 된 것과 동일한 프로세스를 사용 합니다.

MFC에서 제공 하는 모든 창 클래스는 [2 단계 생성을 사용](one-stage-and-two-stage-construction-of-objects.md)합니다. 즉, c + + 연산자를 호출 하는 동안 **`new`** 생성자는 c + + 개체를 할당 하 고 초기화 하지만 해당 Windows 창을 만들지 않습니다. 이렇게 하려면 나중에 window 개체의 [Create](reference/cwnd-class.md#create) member 함수를 호출 합니다.

`Create`멤버 함수는 Windows 창을 만들어 `HWND` c + + 개체의 공용 데이터 멤버 [m_hWnd](reference/cwnd-class.md#m_hwnd)에 저장 합니다. `Create` 는 생성 매개 변수에 대 한 완전 한 유연성을 제공 합니다. 를 호출 하기 전에 `Create` 프레임에 대 한 아이콘 및 클래스 스타일을 설정 하기 위해 [AfxRegisterWndClass](reference/application-information-and-management.md#afxregisterwndclass) 전역 함수를 사용 하 여 창 클래스를 등록할 수 있습니다.

프레임 창의 경우 대신 [Loadframe](reference/cframewnd-class.md#loadframe) 멤버 함수를 사용할 수 있습니다 `Create` . `LoadFrame` Windows 창에서 매개 변수를 덜 사용 하도록 만듭니다. 프레임의 캡션, 아이콘, 액셀러레이터 키 테이블 및 메뉴를 포함 하 여 리소스에서 많은 기본 값을 가져옵니다.

> [!NOTE]
> LoadFrame에서 로드 하려면 아이콘, 액셀러레이터 키 테이블 및 메뉴 리소스에 **IDR_MAINFRAME** 와 같은 공통 리소스 ID가 있어야 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [창 개체](window-objects.md)

- ["클래스" 창 등록](registering-window-classes.md)

- [창 개체 소멸](destroying-window-objects.md)

- [문서 프레임 창 만들기](creating-document-frame-windows.md)

## <a name="see-also"></a>참고 항목

[창 만들기](creating-windows.md)
