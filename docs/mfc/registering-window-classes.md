---
description: '자세히 알아보기: 창 클래스 등록'
title: 창 클래스 등록
ms.date: 11/04/2016
f1_keywords:
- WndProc
helpviewer_keywords:
- window classes [MFC], registering
- registry [MFC], registering classes
- AfxRegisterWndClass method [MFC]
- MFC, windows
- WinMain method [MFC], and registering window classes
- WndProc method [MFC]
- classes [MFC], registering window classes
- WinMain method [MFC]
- registering window classes [MFC]
ms.assetid: 30994bc4-a362-43da-bcc5-1bf67a3fc929
ms.openlocfilehash: e31f83b691ad12d845afca6a3a5f18d9ba64b0e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218194"
---
# <a name="registering-window-classes"></a>창 클래스 등록

Windows 용 기존 프로그래밍의 "클래스" 창에서는 많은 수의 창을 만들 수 있는 "클래스" (c + + 클래스가 아님)의 특성을 정의 합니다. 이러한 종류의 클래스는 창을 만들기 위한 템플릿 또는 모델입니다.

## <a name="window-class-registration-in-traditional-programs-for-windows"></a>Windows 용 기존 프로그램의 창 클래스 등록

MFC를 사용 하지 않고 Windows 용 기존 프로그램에서 "창 프로시저" 또는 ""의 창에 모든 메시지를 처리 `WndProc` 합니다. 는 `WndProc` "창 클래스 등록" 프로세스를 통해 창과 연결 됩니다. 주 창은 함수에 등록 `WinMain` 되지만 다른 windows 클래스는 응용 프로그램의 어느 위치에 나 등록할 수 있습니다. 등록은 `WndProc` 커서, 배경 브러시 등의 사양과 함께 함수에 대 한 포인터를 포함 하는 구조에 따라 달라 집니다. 구조체는 함수에 대 한 이전 호출에서 클래스의 문자열 이름과 함께 매개 변수로 전달 됩니다 `RegisterClass` . 따라서 여러 windows에서 등록 클래스를 공유할 수 있습니다.

## <a name="window-class-registration-in-mfc-programs"></a>MFC 프로그램의 창 클래스 등록

반면 대부분의 window 클래스 등록 활동은 MFC 프레임 워크 프로그램에서 자동으로 수행 됩니다. MFC를 사용 하는 경우 일반적으로 클래스 상속에 대 한 일반 c + + 구문을 사용 하 여 기존 라이브러리 클래스에서 c + + 창 클래스를 파생 시킵니다. 프레임 워크는 기존 "등록 클래스"를 계속 사용 하며, 필요할 때 사용자를 위해 등록 된 여러 표준 클래스를 제공 합니다. [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) global 함수를 호출 하 고 등록 된 클래스를의 멤버 함수에 전달 하 여 추가 등록 클래스를 등록할 수 있습니다 `Create` `CWnd` . 여기에 설명 된 대로 Windows의 기존 "등록 클래스"는 c + + 클래스와 혼동 하지 않습니다.

자세한 내용은 [Technical Note 1](../mfc/tn001-window-class-registration.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[창 만들기](../mfc/creating-windows.md)
