---
title: 클립보드
ms.date: 11/04/2016
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
ms.openlocfilehash: d405a7bbe15d2658380e19c1c908e57f2e40a574
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508937"
---
# <a name="clipboard"></a>클립보드

이 문서 제품군에서는 MFC 응용 프로그램에서 Windows 클립보드에 대 한 지원을 구현 하는 방법을 설명 합니다. Windows 클립보드는 다음과 같은 두 가지 방법으로 사용 됩니다.

- 잘라내기, 복사, 붙여넣기 등의 표준 편집 메뉴 명령을 구현 합니다.

- 끌어서 놓기 (OLE)를 사용 하 여 균일 한 데이터 전송 구현.

클립보드는 소스와 대상 간에 데이터를 전송 하는 표준 Windows 메서드입니다. OLE 작업에서 매우 유용할 수도 있습니다. OLE의 등장으로 Windows에는 두 개의 클립보드 메커니즘이 있습니다. 표준 Windows 클립보드 API는 계속 사용할 수 있지만 OLE 데이터 전송 메커니즘을 사용 하 여 보완 되었습니다. OLE UDT (uniform data transfer)는 클립보드와 끌어서 놓기를 사용 하 여 잘라내기, 복사 및 붙여넣기를 지원 합니다.

클립보드는 전체 Windows 세션에서 공유 하는 시스템 서비스 이므로 자체의 핸들 또는 클래스를 포함 하지 않습니다. [CWnd](../mfc/reference/cwnd-class.md)클래스의 멤버 함수를 통해 클립보드를 관리 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아볼 항목

- [각 클립보드 메커니즘을 사용 하는 경우](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)

- [기존 Windows 클립보드 API 사용](../mfc/clipboard-using-the-windows-clipboard.md)

- [OLE 클립보드 메커니즘 사용](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

- [데이터 복사 및 붙여넣기](../mfc/clipboard-copying-and-pasting-data.md)

- [다른 형식 추가](../mfc/clipboard-adding-other-formats.md)

- [Windows 클립보드](/windows/win32/dataxchg/clipboard)

- [끌어서 놓기 구현 (OLE)](../mfc/drag-and-drop-ole.md)

## <a name="see-also"></a>참고자료

[사용자 인터페이스 요소](../mfc/user-interface-elements-mfc.md)
