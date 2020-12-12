---
description: '자세히 알아보기: 대화 상자 삭제'
title: 대화 상자 소멸시키기
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
ms.openlocfilehash: f46c86e5f3e869f321b8306470e5821658ceafcb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327848"
---
# <a name="destroying-the-dialog-box"></a>대화 상자 소멸시키기

모달 대화 상자는 일반적으로 스택 프레임에서 만들어지고 해당 대화 상자를 만든 함수가 종료 될 때 소멸 됩니다. 대화 상자 개체의 소멸자는 개체가 범위를 벗어날 때 호출 됩니다.

모덜리스 대화 상자는 일반적으로 부모 뷰나 프레임 창 (응용 프로그램의 주 프레임 창 또는 문서 프레임 창)에서 만들고 소유 합니다. 기본 [OnClose](reference/cwnd-class.md#onclose) 처리기는 대화 상자 창을 소멸 시키는 [DestroyWindow](reference/cwnd-class.md#destroywindow)를 호출 합니다. 대화 상자가 단독으로 표시 되거나 그 밖의 특별 한 소유권 의미 체계에 대 한 포인터가 없는 경우 [PostNcDestroy](reference/cwnd-class.md#postncdestroy) 를 재정의 하 여 c + + 대화 상자 개체를 제거 해야 합니다. 또한 [OnCancel](reference/cdialog-class.md#oncancel) 를 재정의 하 고 `DestroyWindow` 내부에서를 호출 해야 합니다. 그렇지 않으면 대화 상자의 소유자가 더 이상 필요 하지 않은 c + + 개체를 제거 해야 합니다.

## <a name="see-also"></a>참고 항목

[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)
