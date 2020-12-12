---
description: '자세히 알아보기: CFolderPickerDialog 클래스'
title: CFolderPickerDialog 클래스
ms.date: 03/27/2019
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
ms.openlocfilehash: f4a5bcc3162a5fffcc723d7ec420685b02be10f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184428"
---
# <a name="cfolderpickerdialog-class"></a>CFolderPickerDialog 클래스

CFolderPickerDialog 클래스는 폴더 선택 모드에서 CFileDialog를 구현 합니다.

## <a name="syntax"></a>구문

```
class CFolderPickerDialog : public CFileDialog;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFolderPickerDialog:: ~ CFolderPickerDialog](#_dtorcfolderpickerdialog)|소멸자|
|[CFolderPickerDialog:: CFolderPickerDialog](#cfolderpickerdialog)|생성자입니다.|

## <a name="remarks"></a>설명

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[CFileDialog](../../mfc/reference/cfiledialog-class.md)

`CFolderPickerDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxdlgs

## <a name="cfolderpickerdialogcfolderpickerdialog"></a><a name="cfolderpickerdialog"></a> CFolderPickerDialog:: CFolderPickerDialog

생성자입니다.

```
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL,
    DWORD dwSize = 0);
```

### <a name="parameters"></a>매개 변수

*lpszFolder*<br/>
초기 폴더.

*dwFlags*<br/>
대화 상자를 사용자 지정할 수 있는 하나 이상의 플래그 조합입니다.

*pParentWnd*<br/>
대화 상자 개체의 부모 또는 소유자 창에 대 한 포인터입니다.

*dwSize*<br/>
OPENFILENAME 구조체의 크기입니다.

### <a name="remarks"></a>설명

## <a name="cfolderpickerdialogcfolderpickerdialog"></a><a name="_dtorcfolderpickerdialog"></a> CFolderPickerDialog:: ~ CFolderPickerDialog

소멸자

```
virtual ~CFolderPickerDialog();
```

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
