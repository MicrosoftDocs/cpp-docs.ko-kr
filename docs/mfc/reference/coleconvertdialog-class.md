---
description: '자세히 알아보기: COleConvertDialog 클래스'
title: COleConvertDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
ms.openlocfilehash: be0b1e88868918b623874cd5691c21752e7af47c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227469"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog 클래스

자세한 내용은 Windows SDK [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) 구조체를 참조 하세요.

## <a name="syntax"></a>구문

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|`COleConvertDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleConvertDialog::D oConvert](#doconvert)|대화 상자에 지정 된 변환을 수행 합니다.|
|[COleConvertDialog::D oModal](#domodal)|OLE 항목 변경 대화 상자를 표시 합니다.|
|[COleConvertDialog:: GetClassID](#getclassid)|선택 된 항목과 연결 된 CLSID를 가져옵니다.|
|[COleConvertDialog:: GetDrawAspect](#getdrawaspect)|항목을 아이콘으로 그릴지 여부를 지정 합니다.|
|[COleConvertDialog:: GetIconicMetafile 파일](#geticonicmetafile)|이 항목의 아이콘 폼과 연결 된 메타 파일에 대 한 핸들을 가져옵니다.|
|[COleConvertDialog:: GetSelectionType](#getselectiontype)|선택한 선택의 유형을 가져옵니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[COleConvertDialog:: m_cv](#m_cv)|대화 상자의 동작을 제어 하는 구조체입니다.|

## <a name="remarks"></a>설명

> [!NOTE]
> 응용 프로그램 마법사에서 생성 된 컨테이너 코드는이 클래스를 사용 합니다.

OLE 관련 대화 상자에 대 한 자세한 내용은 [ole의 아티클 대화 상자](../../mfc/dialog-boxes-in-ole.md)를 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxodlgs

## <a name="coleconvertdialogcoleconvertdialog"></a><a name="coleconvertdialog"></a> COleConvertDialog::COleConvertDialog

`COleConvertDialog`개체만 생성 합니다.

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*pItem*<br/>
변환 하거나 활성화할 항목을 가리킵니다.

*dwFlags*<br/>
비트 or 연산자를 사용 하 여 결합 된 다음 값을 포함 하는 생성 플래그입니다.

- CF_SELECTCONVERTTO 대화 상자를 호출할 때 라디오 단추로 변환 단추를 처음으로 선택 하도록 지정 합니다. 이것이 기본값입니다.

- CF_SELECTACTIVATEAS 대화 상자를 호출할 때 처음으로 활성화 라디오 단추를 선택 하도록 지정 합니다.

- CF_SETCONVERTDEFAULT `clsidConvertDefault` 로 변환 단추를 선택 하면 구조체의 멤버에 의해 CLSID가 지정 된 클래스가 `m_cv` 클래스 목록 상자에서 기본 선택 항목으로 사용 되도록 지정 합니다.

- CF_SETACTIVATEDEFAULT 활성화 된 라디오 단추를 선택 하면 구조체의 멤버에 의해 CLSID가 지정 된 클래스가 `clsidActivateDefault` `m_cv` 클래스 목록 상자에서 기본 선택 항목으로 사용 되도록 지정 합니다.

- CF_SHOWHELPBUTTON 대화 상자를 호출할 때 도움말 단추가 표시 되도록 지정 합니다.

*pClassID*<br/>
변환 하거나 활성화할 항목의 CLSID를 가리킵니다. NULL 인 경우 *Pitem* 과 연결 된 CLSID가 사용 됩니다.

*pParentWnd*<br/>
대화 상자 개체가 속한 부모 또는 소유자 창 개체 (형식 `CWnd` )를 가리킵니다. NULL 인 경우에는 대화 상자의 부모 창이 주 응용 프로그램 창으로 설정 됩니다.

### <a name="remarks"></a>설명

대화 상자를 표시 하려면 [DoModal](#domodal) 함수를 호출 합니다.

자세한 내용은 [CLSID Key](/windows/win32/com/clsid-key-hklm) 및 [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) 구조체를 참조 하세요.

## <a name="coleconvertdialogdoconvert"></a><a name="doconvert"></a> COleConvertDialog::D oConvert

[DoModal](#domodal)에서 성공적으로 반환 된 후 또는를 변환 하 여 [COleClientItem](../../mfc/reference/coleclientitem-class.md)형식의 개체를 활성화 한 후이 함수를 호출 합니다.

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>매개 변수

*pItem*<br/>
변환 하거나 활성화할 항목을 가리킵니다. NULL이 될 수 없습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

항목은 변환 대화 상자에서 사용자가 선택한 정보에 따라 변환 되거나 활성화 됩니다.

## <a name="coleconvertdialogdomodal"></a><a name="domodal"></a> COleConvertDialog::D oModal

OLE 변환 대화 상자를 표시 하려면이 함수를 호출 합니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

대화 상자의 완료 상태입니다. 다음 값 중 하나입니다.

- 대화 상자가 성공적으로 표시 되 면 IDOK입니다.

- 사용자가 대화 상자를 취소 한 경우 IDCANCEL입니다.

- 오류가 발생 한 경우 IDABORT입니다. IDABORT가 반환 되 면 [Coledialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) 멤버 함수를 호출 하 여 발생 한 오류 유형에 대 한 자세한 정보를 가져옵니다. 가능한 오류 목록은 Windows SDK에서 [OleUIConvert](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw) 함수를 참조 하세요.

### <a name="remarks"></a>설명

[M_cv](#m_cv) 구조의 멤버를 설정 하 여 다양 한 대화 상자 컨트롤을 초기화 하려면를 호출 하기 전에이 작업을 수행 해야 합니다 `DoModal` . 대화 상자 개체가 생성 된 후에는이 작업을 수행 해야 합니다.

`DoModal`에서 IDOK를 반환 하는 경우 다른 멤버 함수를 호출 하 여 대화 상자에 사용자가 입력 한 설정이 나 정보를 검색할 수 있습니다.

## <a name="coleconvertdialoggetclassid"></a><a name="getclassid"></a> COleConvertDialog:: GetClassID

변환 대화 상자에서 사용자가 선택한 항목과 연결 된 CLSID를 가져오려면이 함수를 호출 합니다.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>반환 값

변환 대화 상자에서 선택한 항목과 연결 된 CLSID입니다.

### <a name="remarks"></a>설명

[DoModal](#domodal) 가 IDOK를 반환한 후에만이 함수를 호출 합니다.

자세한 내용은 Windows SDK의 [CLSID 키](/windows/win32/com/clsid-key-hklm) 를 참조 하세요.

## <a name="coleconvertdialoggetdrawaspect"></a><a name="getdrawaspect"></a> COleConvertDialog:: GetDrawAspect

사용자가 선택한 항목을 아이콘으로 표시 하도록 선택 했는지 여부를 확인 하려면이 함수를 호출 합니다.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>반환 값

개체를 렌더링 하는 데 필요한 메서드입니다.

- 아이콘으로 표시 확인란을 선택 하지 않은 경우 DVASPECT_CONTENT 반환 됩니다.

- 아이콘으로 표시 확인란을 선택 하면 DVASPECT_ICON 반환 됩니다.

### <a name="remarks"></a>설명

[DoModal](#domodal) 가 IDOK를 반환한 후에만이 함수를 호출 합니다.

모양 그리기에 대 한 자세한 내용은 Windows SDK의 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 데이터 구조를 참조 하세요.

## <a name="coleconvertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a> COleConvertDialog:: GetIconicMetafile 파일

이 함수를 호출 하 여 선택한 항목의 아이콘 측면을 포함 하는 메타 파일에 대 한 핸들을 가져옵니다.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>반환 값

확인을 선택 하 여 대화 상자를 닫을 때 아이콘으로 표시 확인란이 선택 된 경우 선택한 항목의 아이콘 측면을 포함 하는 메타 파일에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

## <a name="coleconvertdialoggetselectiontype"></a><a name="getselectiontype"></a> COleConvertDialog:: GetSelectionType

변환 대화 상자에서 선택한 변환 유형을 확인 하려면이 함수를 호출 합니다.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>반환 값

선택 항목의 유형입니다.

### <a name="remarks"></a>설명

반환 형식 값은 `Selection` 클래스에 선언 된 열거형 형식에 의해 지정 됩니다 `COleConvertDialog` .

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

이러한 값에 대 한 간략 한 설명은 다음과 같습니다.

- `COleConvertDialog::noConversion` 대화 상자가 취소 되었거나 사용자가 변환을 선택 하지 않은 경우 반환 됩니다. IDOK이 반환 되는 경우 `COleConvertDialog::DoModal` 사용자가 이전에 선택한 것과 다른 아이콘을 선택할 수 있습니다.

- `COleConvertDialog::convertItem` 라디오 단추로 변환 단추가 선택 되어 있고 사용자가 변환할 다른 항목을 선택 하 고 IDOK를 반환 하면 반환 `DoModal` 됩니다.

- `COleConvertDialog::activateAs` 활성화 된 라디오 단추를 선택 하 고 사용자가 활성화할 다른 항목을 선택 하 고 IDOK를 반환 하면 반환 `DoModal` 됩니다.

## <a name="coleconvertdialogm_cv"></a><a name="m_cv"></a> COleConvertDialog:: m_cv

Convert 대화 상자의 동작을 제어 하는 데 사용 되는 OLEUICONVERT 형식의 구조입니다.

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>설명

이 구조체의 멤버는 직접 또는 멤버 함수를 통해 수정할 수 있습니다.

자세한 내용은 Windows SDK [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) 구조체를 참조 하세요.

## <a name="see-also"></a>참고 항목

[COleDialog 클래스](../../mfc/reference/coledialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 클래스](../../mfc/reference/coledialog-class.md)
