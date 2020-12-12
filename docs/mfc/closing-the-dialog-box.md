---
description: '자세히 알아보기: 대화 상자 닫기'
title: 대화 상자 닫기
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 4e60bdfb1ecb6968996d6c657f0c667ad2686a56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338370"
---
# <a name="closing-the-dialog-box"></a>대화 상자 닫기

사용자가 단추 중 하나를 선택 하면 모달 대화 상자가 닫힙니다. 일반적으로 확인 단추나 취소 단추입니다. 확인 또는 취소 단추를 선택 하면 Windows에서 단추 ID ( **IDOK** 또는 **IDCANCEL**)를 사용 하 여 대화 상자 개체 **BN_CLICKED** 컨트롤 알림 메시지를 보냅니다. `CDialog` 는 및 메시지에 대 한 기본 처리기 함수를 제공 `OnOK` `OnCancel` 합니다. 기본 처리기는 `EndDialog` 멤버 함수를 호출 하 여 대화 상자 창을 닫습니다. 사용자의 코드에서을 호출할 수도 있습니다 `EndDialog` . 자세한 내용은 MFC 참조에서 클래스의 [EndDialog](reference/cdialog-class.md#enddialog) 멤버 함수를 참조 `CDialog` 하세요 .

모덜리스 대화 상자를 닫고 삭제 하기 위해를 정렬 하려면 `PostNcDestroy` 포인터에서 연산자를 재정의 하 고 호출 **`delete`** **`this`** 합니다. [대화 상자를 삭제 하면](destroying-the-dialog-box.md) 다음에 발생 하는 결과가 설명 됩니다.

## <a name="see-also"></a>참고 항목

[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)
