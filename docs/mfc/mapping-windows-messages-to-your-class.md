---
description: '자세히 알아보기: 클래스에 Windows 메시지 매핑'
title: 클래스에 Windows 메시지 매핑
ms.date: 09/06/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
- Class Wizard [MFC]
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: cca13c4b262c6373fa3d968438331d5e0ce5f7d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280783"
---
# <a name="mapping-windows-messages-to-your-class"></a>클래스에 Windows 메시지 매핑

Windows 메시지를 처리 하는 대화 상자가 필요한 경우 적절 한 처리기 함수를 재정의 합니다. 이렇게 하려면 **솔루션 탐색기** 에서 **클래스 뷰** 탭을 선택 하 고 대화 상자를 나타내는 클래스를 마우스 오른쪽 단추로 클릭 한 다음 [클래스 마법사](reference/mfc-class-wizard.md)를 선택 합니다. 마법사를 사용 하 여 대화 상자 클래스에 [메시지를 매핑할](reference/mapping-messages-to-functions.md) 수 있습니다. 그러면 각 메시지에 대 한 메시지 맵 항목이 작성 되 고 클래스에 메시지 처리기 멤버 함수가 추가 됩니다. 코드 편집기를 사용 하 여 메시지 처리기에서 코드를 작성 합니다.

또한 [CDialog](reference/cdialog-class.md) 의 멤버 함수와 특히 [CWnd](reference/cwnd-class.md)의 기본 클래스를 재정의할 수 있습니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [메시지 처리 및 매핑](message-handling-and-mapping.md)

- [일반적으로 재정의되는 멤버 함수](commonly-overridden-member-functions.md)

- [일반적으로 추가되는 멤버 함수](commonly-added-member-functions.md)

## <a name="see-also"></a>참고 항목

[대화 상자](dialog-boxes.md)<br/>
[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)
