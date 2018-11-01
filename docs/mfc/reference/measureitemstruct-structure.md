---
title: MEASUREITEMSTRUCT 구조체
ms.date: 11/04/2016
f1_keywords:
- MEASUREITEMSTRUCT
helpviewer_keywords:
- MEASUREITEMSTRUCT structure [MFC]
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
ms.openlocfilehash: 3f541c30c484041d855807f220345d6863a780d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575053"
---
# <a name="measureitemstruct-structure"></a>MEASUREITEMSTRUCT 구조체

`MEASUREITEMSTRUCT` 구조에 소유자가 그린 컨트롤 또는 메뉴 항목의 크기의 Windows에 알립니다.

## <a name="syntax"></a>구문

```
typedef struct tagMEASUREITEMSTRUCT {
    UINT CtlType;
    UINT CtlID;
    UINT itemID;
    UINT itemWidth;
    UINT itemHeight;
    DWORD itemData
} MEASUREITEMSTRUCT;
```

#### <a name="parameters"></a>매개 변수

*CtlType*<br/>
컨트롤 형식을 포함합니다. 컨트롤 형식의 값은 다음과 같습니다.

- ODT_COMBOBOX 소유자 그리기 콤보 상자

- ODT_LISTBOX 소유자 그리기 목록 상자

- ODT_MENU 소유자 그리기 메뉴

*CtlID*<br/>
단추, 목록 상자 또는 콤보 상자 컨트롤 ID를 포함합니다. 이 멤버는 메뉴에 사용되지 않습니다.

*itemID*<br/>
메뉴의 메뉴 항목 ID 또는 가변 높이 콤보 상자 또는 목록 상자에 대 한 목록 상자 항목 ID를 포함합니다. 이 멤버는 고정 높이 콤보 상자 또는 목록 상자 또는 단추에 대 한 사용 되지 않습니다.

*itemWidth*<br/>
메뉴 항목의 너비를 지정합니다. 소유자 그리기 메뉴 항목의 소유자는 메시지에서 반환 하기 전에이 멤버를 입력 해야 합니다.

*으로 itemHeight*<br/>
목록 상자 또는 메뉴에 있는 개별 항목의 높이 지정합니다. 소유자 그리기 콤보 상자의 소유자는 메시지에서 반환 하기 전에이 멤버 목록 상자 또는 메뉴 항목 입력 해야 합니다. 목록 상자 항목의 최대 높이 255입니다.

*itemData*<br/>
콤보 상자 또는 목록 상자의 경우 이 멤버는 다음 중 하나에 의해 목록 상자에 전달된 값을 포함합니다.

- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)

- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)

- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)

- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)

메뉴의 경우 이 멤버는 다음 중 하나에 의해 메뉴에 전달된 값을 포함합니다.

- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)

- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)

- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)

이렇게 하면 Windows 컨트롤을 사용 하 여 사용자 상호 작용을 올바르게 처리할 수 있습니다. 적절 한 멤버를 작성 하는 오류를 `MEASUREITEMSTRUCT` 구조에는 컨트롤의 부적절 한 작업이 실행 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:** winuser.h

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)

