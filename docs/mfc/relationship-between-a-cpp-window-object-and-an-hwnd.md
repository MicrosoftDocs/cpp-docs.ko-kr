---
description: '자세한 정보: c + + 창 개체와 HWND 간 관계'
title: C++ 창 개체와 HWND 간 관계
ms.date: 11/19/2018
f1_keywords:
- HWND
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
ms.openlocfilehash: bdcf52d2890265b854e3eef7854b489b47eda6a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218097"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>C++ 창 개체와 HWND 간 관계

Window *개체* 는 프로그램에서 직접 만드는 c + + `CWnd` 클래스 또는 파생 클래스의 개체입니다. 프로그램의 생성자와 소멸자 호출에 대 한 응답으로 제공 됩니다. 반면에 Windows *창은* 창에 해당 하는 내부 windows 데이터 구조에 대 한 불투명 핸들이 며 있을 때 시스템 리소스를 소비 합니다. Windows 창은 "창 핸들" ()으로 식별 되며 `HWND` , `CWnd` `Create` 클래스의 멤버 함수를 호출 하 여 개체를 만든 후에 만들어집니다 `CWnd` . 프로그램 호출 또는 사용자의 작업을 통해 창이 소멸 될 수 있습니다. 창 핸들은 창 개체의 *m_hWnd* 멤버 변수에 저장 됩니다. 다음 그림에서는 c + + 창 개체와 Windows 창 간의 관계를 보여 줍니다. Windows 만들기에 대 한 자세한 내용은 [windows](../mfc/creating-windows.md)를 만드는 방법을 설명 합니다. 창 소멸은 [창 개체](../mfc/destroying-window-objects.md)제거에 설명 되어 있습니다.

![CWnd 창 개체 및 결과 창](../mfc/media/vc37fj1.gif "CWnd 창 개체 및 결과 창") <br/>
창 개체 및 Windows 창

## <a name="see-also"></a>참고 항목

[창 개체](../mfc/window-objects.md)
