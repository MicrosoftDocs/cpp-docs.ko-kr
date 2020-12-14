---
description: '자세히 알아보기: COleLinksDialog 클래스'
title: COleLinksDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
ms.openlocfilehash: 036fc2b97fe4ad529e87c3573e280c99ac157848
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226924"
---
# <a name="colelinksdialog-class"></a>COleLinksDialog 클래스

OLE 링크 편집 대화 상자에 사용합니다.

## <a name="syntax"></a>구문

```
class COleLinksDialog : public COleDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|`COleLinksDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleLinksDialog::DoModal](#domodal)|OLE 링크 편집 대화 상자를 표시 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|대화 상자의 동작을 제어 하는 OLEUIEDITLINKS 형식의 구조체입니다.|

## <a name="remarks"></a>설명

`COleLinksDialog`이 대화 상자를 호출 하려면 클래스의 개체를 만듭니다. `COleLinksDialog` 개체를 생성 한 후에는 [m_el](#m_el) 구조를 사용하여 대화 상자에서 컨트롤의 값 또는 상태를 초기화할 수 있습니다. `m_el`구조는 OLEUIEDITLINKS 형식입니다. 이 대화 상자 클래스를 사용 하는 방법에 대 한 자세한 내용은 [DoModal](#domodal) 멤버 함수를 참조 하세요.

> [!NOTE]
> 응용 프로그램 마법사에서 생성 된 컨테이너 코드는이 클래스를 사용 합니다.

자세한 내용은 Windows SDK [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) 구조체를 참조 하세요.

OLE 관련 대화 상자에 대 한 자세한 내용은 [ole의 아티클 대화 상자](../../mfc/dialog-boxes-in-ole.md)를 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxodlgs

## <a name="colelinksdialogdomodal"></a><a name="domodal"></a> COleLinksDialog::D oModal

OLE 링크 편집 대화 상자를 표시 합니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

대화 상자의 완료 상태입니다. 다음 값 중 하나입니다.

- 대화 상자가 성공적으로 표시 되 면 IDOK입니다.

- 사용자가 대화 상자를 취소 한 경우 IDCANCEL입니다.

- 오류가 발생 한 경우 IDABORT입니다. IDABORT가 반환 되는 경우 `COleDialog::GetLastError` 멤버 함수를 호출 하 여 발생 한 오류 유형에 대 한 자세한 정보를 얻습니다. 가능한 오류 목록은 Windows SDK에서 [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) 함수를 참조 하세요.

### <a name="remarks"></a>설명

[M_el](#m_el) 구조의 멤버를 설정 하 여 다양 한 대화 상자 컨트롤을 초기화 하려면를 호출 하기 전에이 작업을 수행 해야 합니다 `DoModal` . 대화 상자 개체가 생성 된 후에는을 호출 해야 합니다.

## <a name="colelinksdialogcolelinksdialog"></a><a name="colelinksdialog"></a> COleLinksDialog::COleLinksDialog

`COleLinksDialog` 개체를 생성합니다.

```
COleLinksDialog (
    COleDocument* pDoc,
    CView* pView,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*pDoc*<br/>
편집할 링크를 포함 하는 OLE 문서를 가리킵니다.

*pView*<br/>
*Pdoc* 의 현재 보기를 가리킵니다.

*dwFlags*<br/>
대화 상자가 표시 될 때 도움말 단추가 표시 되는지 여부를 지정 하는 0 또는 ELF_SHOWHELP 포함 하는 생성 플래그입니다.

*pParentWnd*<br/>
대화 상자 개체가 속한 부모 또는 소유자 창 개체 (형식 `CWnd` )를 가리킵니다. NULL 인 경우에는 대화 상자의 부모 창이 주 응용 프로그램 창으로 설정 됩니다.

### <a name="remarks"></a>설명

이 함수는 개체만 생성 `COleLinksDialog` 합니다. 대화 상자를 표시 하려면 [DoModal](#domodal) 함수를 호출 합니다.

## <a name="colelinksdialogm_el"></a><a name="m_el"></a> COleLinksDialog:: m_el

링크 편집 대화 상자의 동작을 제어 하는 데 사용 되는 OLEUIEDITLINKS 형식의 구조입니다.

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>설명

이 구조체의 멤버는 직접 또는 멤버 함수를 통해 수정할 수 있습니다.

자세한 내용은 Windows SDK [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) 구조체를 참조 하세요.

## <a name="see-also"></a>참고 항목

[COleDialog 클래스](../../mfc/reference/coledialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 클래스](../../mfc/reference/coledialog-class.md)
