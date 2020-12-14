---
description: '자세히 알아보기: CCommonDialog 클래스'
title: CCommonDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
ms.openlocfilehash: 927348982529f14eb0ad762019bb4463aaa77c99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227899"
---
# <a name="ccommondialog-class"></a>CCommonDialog 클래스

Windows 공용 대화 상자의 기능을 캡슐화하는 클래스의 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class CCommonDialog : public CDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CCommonDialog::CCommonDialog](#ccommondialog)|`CCommonDialog` 개체를 생성합니다.|

## <a name="remarks"></a>설명

다음 클래스는 Windows 공용 대화 상자의 기능을 캡슐화 합니다.

- [CFileDialog](../../mfc/reference/cfiledialog-class.md)

- [CFontDialog](../../mfc/reference/cfontdialog-class.md)

- [CColorDialog](../../mfc/reference/ccolordialog-class.md)

- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)

- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)

- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)

- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)

- [COleDialog](../../mfc/reference/coledialog-class.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CCommonDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxdlgs

## <a name="ccommondialogccommondialog"></a><a name="ccommondialog"></a> CCommonDialog::CCommonDialog

`CCommonDialog` 개체를 생성합니다.

```
explicit CCommonDialog(CWnd* pParentWnd);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
Dialog 개체가 속한 부모 또는 소유자 창 개체 ( [CWnd](../../mfc/reference/cwnd-class.md)형식)를 가리킵니다. NULL 인 경우에는 대화 상자 개체의 부모 창이 주 응용 프로그램 창으로 설정 됩니다.

### <a name="remarks"></a>설명

전체 정보는 [cdialog:: cdialog](../../mfc/reference/cdialog-class.md#cdialog) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CDialog 클래스](../../mfc/reference/cdialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CFileDialog 클래스](../../mfc/reference/cfiledialog-class.md)<br/>
[CFontDialog 클래스](../../mfc/reference/cfontdialog-class.md)<br/>
[CColorDialog 클래스](../../mfc/reference/ccolordialog-class.md)<br/>
[CPageSetupDialog 클래스](../../mfc/reference/cpagesetupdialog-class.md)<br/>
[CPrintDialog 클래스](../../mfc/reference/cprintdialog-class.md)<br/>
[CFindReplaceDialog 클래스](../../mfc/reference/cfindreplacedialog-class.md)<br/>
[COleDialog 클래스](../../mfc/reference/coledialog-class.md)
