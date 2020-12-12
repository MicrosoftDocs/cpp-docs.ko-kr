---
description: '자세히 알아보기: COleUpdateDialog 클래스'
title: COleUpdateDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
ms.openlocfilehash: e7f1d1e7f67fd80fd7042e53a7ccdee46dc6531f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226599"
---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog 클래스

OLE 편집 링크 대화 상자의 특별한 경우에 사용됩니다. 예를 들어, 문서에서 기존에 연결되거나 포함된 개체만 업데이트할 경우에 사용해야 합니다.

## <a name="syntax"></a>구문

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleUpdateDialog:: COleUpdateDialog](#coleupdatedialog)|`COleUpdateDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleUpdateDialog::D oModal](#domodal)|업데이트 모드에서 **링크 편집** 대화 상자를 표시 합니다.|

## <a name="remarks"></a>설명

OLE 관련 대화 상자에 대 한 자세한 내용은 [ole의 아티클 대화 상자](../../mfc/dialog-boxes-in-ole.md)를 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxodlgs

## <a name="coleupdatedialogcoleupdatedialog"></a><a name="coleupdatedialog"></a> COleUpdateDialog:: COleUpdateDialog

`COleUpdateDialog` 개체를 생성합니다.

```
explicit COleUpdateDialog(
    COleDocument* pDoc,
    BOOL bUpdateLinks = TRUE,
    BOOL bUpdateEmbeddings = FALSE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*pDoc*<br/>
업데이트 해야 할 수 있는 링크가 포함 된 문서를 가리킵니다.

*bUpdateLinks*<br/>
연결 된 개체를 업데이트할지 여부를 결정 하는 플래그입니다.

*bUpdateEmbeddings*<br/>
포함 된 개체를 업데이트할지 여부를 결정 하는 플래그입니다.

*pParentWnd*<br/>
대화 상자 개체가 속한 부모 또는 소유자 창 개체 (형식 `CWnd` )를 가리킵니다. NULL 이면 대화 상자의 부모 창이 주 응용 프로그램 창으로 설정 됩니다.

### <a name="remarks"></a>설명

이 함수는 개체만 생성 `COleUpdateDialog` 합니다. 대화 상자를 표시 하려면 [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal)를 호출 합니다. 이 클래스는 `COleLinksDialog` 기존에 연결 되거나 포함 된 항목만 업데이트 하려는 경우 대신 사용 해야 합니다.

## <a name="coleupdatedialogdomodal"></a><a name="domodal"></a> COleUpdateDialog::D oModal

업데이트 모드에서 링크 편집 대화 상자를 표시 합니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

대화 상자의 완료 상태입니다. 다음 값 중 하나입니다.

- 대화 상자가 성공적으로 반환 되 면 IDOK을 반환 합니다.

- 현재 문서에 있는 연결 된 항목 또는 포함 된 항목 중 업데이트가 필요 하지 않은 경우에는 IDCANCEL입니다.

- 오류가 발생 한 경우 IDABORT입니다. IDABORT가 반환 되 면 [Coledialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) 멤버 함수를 호출 하 여 발생 한 오류 유형에 대 한 자세한 정보를 가져옵니다. 가능한 오류 목록은 Windows SDK에서 [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) 함수를 참조 하세요.

### <a name="remarks"></a>설명

사용자가 취소 단추를 선택 하지 않으면 모든 링크 및/또는 포함가 업데이트 됩니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleLinksDialog 클래스](../../mfc/reference/colelinksdialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog 클래스](../../mfc/reference/colelinksdialog-class.md)
