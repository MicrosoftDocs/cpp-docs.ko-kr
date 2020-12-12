---
description: 'TN070: MFC 창 클래스 이름에 대 한 자세한 정보'
title: 'TN070: MFC 창 클래스 이름'
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: 963f343f480a5805a3c1ec3cf5499583a17535ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214522"
---
# <a name="tn070-mfc-window-class-names"></a>TN070: MFC 창 클래스 이름

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

MFC windows는 창의 기능을 반영 하는 동적으로 생성 된 클래스 이름을 사용 합니다. MFC는 응용 프로그램에서 생성 되는 프레임 창, 뷰 및 팝업 창에 대해 동적으로 클래스 이름을 생성 합니다. MFC 응용 프로그램에 의해 생성 되는 대화 상자와 컨트롤은 해당 창의 클래스에 대해 Windows에서 제공 하는 이름을 갖습니다.

사용자 고유의 창 클래스를 등록 하 고 [Precreatewindow](../mfc/reference/cwnd-class.md#precreatewindow)의 재정의에서 사용 하 여 동적으로 제공 된 클래스 이름을 바꿀 수 있습니다. 해당 MFC 제공 클래스 이름은 다음 두 가지 형식 중 하나에 적합 합니다.

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

문자를 대체 하는 16 진수가 `%x` [예: wndclassa](/windows/win32/api/winuser/ns-winuser-wndclassw) 구조체의 데이터에서 채워집니다. MFC는 동일한 **예: wndclassa** 구조가 필요한 여러 c + + 클래스가 등록 된 동일한 창 클래스를 공유할 수 있도록이 기술을 사용 합니다. 대부분의 간단한 Win32 응용 프로그램과 달리, MFC 응용 프로그램에는 하나의 **WNDPROC** 만 있으므로 **예: wndclassa** 구조체를 쉽게 공유 하 여 시간과 메모리를 절약할 수 있습니다. 위에 표시 된 문자에 대 한 대체 가능 값은 다음과 같습니다 `%x` .

- **예: WNDCLASSA 인스턴스**

- **예: WNDCLASSA**

- **예: WNDCLASSA**

- **예: WNDCLASSA**

- **예: WNDCLASSA 아이콘**

첫 번째 폼 ( `Afx:%x:%x` )은 **hcursor**, **Hbrbackground** 및 **hcursor** 이 모두 **NULL** 일 때 사용 됩니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)<br/>
[TN020: ID 명명 및 번호 매기기 규칙](../mfc/tn020-id-naming-and-numbering-conventions.md)
