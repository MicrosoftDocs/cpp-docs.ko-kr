---
title: 대화 상자 닫기
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 48ea954552b3ea9aa7193a47fc2a66d731312d77
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685378"
---
# <a name="closing-the-dialog-box"></a>대화 상자 닫기

사용자가 단추 중 하나를 선택 하면 모달 대화 상자가 닫힙니다. 일반적으로 확인 단추나 취소 단추입니다. 확인 또는 취소 단추를 선택 하면 Windows에서 단추 ID가 **IDOK** 또는 **IDCANCEL**인 **BN_CLICKED** 컨트롤 알림 메시지를 대화 상자 개체에 보냅니다. `CDialog`은 `OnOK` 및 `OnCancel` 메시지에 대 한 기본 처리기 함수를 제공 합니다. 기본 처리기는 `EndDialog` 멤버 함수를 호출 하 여 대화 상자 창을 닫습니다. 사용자의 코드에서 `EndDialog`을 호출할 수도 있습니다. 자세한 내용은 *MFC 참조*에서 `CDialog` 클래스의 [EndDialog](../mfc/reference/cdialog-class.md#enddialog) 멤버 함수를 참조 하세요.

모덜리스 대화 상자를 닫고 삭제 하기 위해를 정렬 하려면 `PostNcDestroy`을 재정의 하 고 **this** 포인터에서 **delete** 연산자를 호출 합니다. [대화 상자를 삭제 하면](../mfc/destroying-the-dialog-box.md) 다음에 발생 하는 결과가 설명 됩니다.

## <a name="see-also"></a>참조

[MFC에서 대화 상자 작업](../mfc/life-cycle-of-a-dialog-box.md)
