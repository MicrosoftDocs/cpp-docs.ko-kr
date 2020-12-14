---
description: '자세히 알아보기: COlePasteSpecialDialog 클래스'
title: COlePasteSpecialDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
ms.openlocfilehash: b2493fbe7f9894a27b6765cbd5e0bc583d9d4a18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226859"
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog 클래스

OLE 선택하여 붙여넣기 대화 상자에 사용합니다.

## <a name="syntax"></a>구문

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|`COlePasteSpecialDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COlePasteSpecialDialog:: AddFormat](#addformat)|응용 프로그램에서 붙여 넣을 수 있는 형식 목록에 사용자 지정 형식을 추가 합니다.|
|[COlePasteSpecialDialog:: AddLinkEntry](#addlinkentry)|지원 되는 클립보드 형식 목록에 새 항목을 추가 합니다.|
|[COlePasteSpecialDialog:: AddStandardFormats](#addstandardformats)|응용 프로그램에서 붙여 넣을 수 있는 형식 목록에 CF_BITMAP, CF_DIB, CF_METAFILEPICT 및 필요에 따라 CF_LINKSOURCE를 추가 합니다.|
|[COlePasteSpecialDialog:: CreateItem](#createitem)|지정 된 형식을 사용 하 여 컨테이너 문서에 항목을 만듭니다.|
|[COlePasteSpecialDialog::D oModal](#domodal)|OLE 붙여넣기 옵션 대화 상자를 표시 합니다.|
|[COlePasteSpecialDialog:: GetDrawAspect](#getdrawaspect)|항목을 아이콘으로 그릴지 여부를 나타냅니다.|
|[COlePasteSpecialDialog:: GetIconicMetafile 파일](#geticonicmetafile)|이 항목의 아이콘 폼과 연결 된 메타 파일에 대 한 핸들을 가져옵니다.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|사용자가 선택한 사용 가능한 붙여넣기 옵션의 인덱스를 가져옵니다.|
|[COlePasteSpecialDialog:: GetSelectionType](#getselectiontype)|선택한 선택의 유형을 가져옵니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[COlePasteSpecialDialog:: m_ps](#m_ps)|대화 상자의 함수를 제어 하는 OLEUIPASTESPECIAL 형식의 구조체입니다.|

## <a name="remarks"></a>설명

`COlePasteSpecialDialog`이 대화 상자를 호출 하려면 클래스의 개체를 만듭니다. `COlePasteSpecialDialog`개체가 생성 된 후 [addformat](#addformat) 및 [addstandardformats](#addstandardformats) 멤버 함수를 사용 하 여 클립보드 형식을 대화 상자에 추가할 수 있습니다. 또한 [m_ps](#m_ps) 구조를 사용 하 여 대화 상자에서 컨트롤의 값 이나 상태를 초기화할 수 있습니다. `m_ps`구조는 OLEUIPASTESPECIAL 형식입니다.

자세한 내용은 Windows SDK [OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) 구조체를 참조 하세요.

OLE 관련 대화 상자에 대 한 자세한 내용은 [ole의 아티클 대화 상자](../../mfc/dialog-boxes-in-ole.md)를 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxodlgs

## <a name="colepastespecialdialogaddformat"></a><a name="addformat"></a> COlePasteSpecialDialog:: AddFormat

이 함수를 호출 하 여 응용 프로그램이 특수 하 게 붙여넣기 작업에서 지원할 수 있는 형식 목록에 새 형식을 추가 합니다.

```cpp
void AddFormat(
    const FORMATETC& formatEtc,
    LPTSTR lpszFormat,
    LPTSTR lpszResult,
    DWORD flags);

void AddFormat(
    UINT cf,
    DWORD tymed,
    UINT nFormatID,
    BOOL bEnableIcon,
    BOOL bLink);
```

### <a name="parameters"></a>매개 변수

*bcp.fmt*<br/>
추가할 데이터 형식에 대 한 참조입니다.

*lpszFormat*<br/>
사용자의 형식을 설명 하는 문자열입니다.

*lpszResult*<br/>
대화 상자에서이 형식을 선택한 경우 결과를 설명 하는 문자열입니다.

*flags*<br/>
이 형식에 사용할 수 있는 다양 한 연결 및 포함 옵션입니다. 이 플래그는 OLEUIPASTEFLAG 열거 형식에 있는 하나 이상의 다른 값의 비트 조합입니다.

*f*<br/>
추가할 클립보드 형식입니다.

*tymed*<br/>
이 형식으로 사용할 수 있는 미디어의 유형입니다. TYMED 열거 형식에 있는 하나 이상의 값에 대 한 비트 조합입니다.

*nFormatID*<br/>
이 형식을 식별 하는 문자열의 ID입니다. 이 문자열의 형식은 ' \n ' 문자로 구분 된 두 개의 개별 문자열입니다. 첫 번째 문자열은 *Lpstrformat* 매개 변수에 전달 되는 것과 같으며 두 번째 문자열은 *lpstrformat* 매개 변수와 같습니다.

*베 아이콘*<br/>
목록 상자에서이 형식을 선택할 때 아이콘으로 표시 확인란을 사용할 수 있는지 여부를 결정 하는 플래그입니다.

*불빛이*<br/>
목록 상자에서이 형식을 선택할 때 링크 붙여넣기 라디오 단추를 사용할 수 있는지 여부를 결정 하는 플래그입니다.

### <a name="remarks"></a>설명

이 함수를 호출 하 여 CF_TEXT 또는 CF_TIFF 같은 표준 형식이 나 응용 프로그램이 시스템에 등록 한 사용자 지정 형식을 추가할 수 있습니다. 데이터 개체를 응용 프로그램에 붙여 넣는 방법에 대 한 자세한 내용은 [데이터 개체 및 데이터 소스: 조작](../../mfc/data-objects-and-data-sources-manipulation.md)문서를 참조 하세요.

자세한 내용은 Windows SDK [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) 열거형 형식 및 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 참조 하세요.

자세한 내용은 Windows SDK에서 [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) 열거 형식을 참조 하십시오.

## <a name="colepastespecialdialogaddlinkentry"></a><a name="addlinkentry"></a> COlePasteSpecialDialog:: AddLinkEntry

지원 되는 클립보드 형식 목록에 새 항목을 추가 합니다.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>매개 변수

*f*<br/>
추가할 클립보드 형식입니다.

### <a name="return-value"></a>반환 값

새 링크 항목에 대 한 정보를 포함 하는 [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) 구조체입니다.

## <a name="colepastespecialdialogaddstandardformats"></a><a name="addstandardformats"></a> COlePasteSpecialDialog:: AddStandardFormats

이 함수를 호출 하 여 다음 클립보드 형식을 응용 프로그램이 특수 한 붙여넣기 작업에서 지원할 수 있는 형식 목록에 추가 합니다.

```cpp
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>매개 변수

*베*<br/>
응용 프로그램에서 붙여 넣을 수 있는 형식 목록에 CF_LINKSOURCE를 추가할지 여부를 결정 하는 플래그입니다.

### <a name="remarks"></a>설명

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"포함 개체"**

- 생략할 **"링크 소스"**

이러한 형식은 포함 및 연결을 지 원하는 데 사용 됩니다.

## <a name="colepastespecialdialogcolepastespecialdialog"></a><a name="colepastespecialdialog"></a> COlePasteSpecialDialog::COlePasteSpecialDialog

`COlePasteSpecialDialog` 개체를 생성합니다.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*dwFlags*<br/>
생성 플래그에는 비트 or 연산자를 사용 하 여 결합 된 다음 플래그의 개수가 포함 됩니다.

- PSF_SELECTPASTE 대화 상자를 호출할 때 붙여넣기 라디오 단추가 처음에 선택 되도록 지정 합니다. PSF_SELECTPASTELINK와 함께 사용할 수 없습니다. 이것이 기본값입니다.

- PSF_SELECTPASTELINK 대화 상자를 호출할 때 링크 붙여넣기 라디오 단추가 처음에 선택 되도록 지정 합니다. PSF_SELECTPASTE와 함께 사용할 수 없습니다.

- PSF_CHECKDISPLAYASICON 대화 상자를 호출할 때 아이콘으로 표시 확인란을 처음에 선택 하도록 지정 합니다.

- PSF_SHOWHELP 대화 상자를 호출할 때 도움말 단추가 표시 되도록 지정 합니다.

*pDataObject*<br/>
붙여 넣을 [Coledataobject](../../mfc/reference/coledataobject-class.md) 를 가리킵니다. 이 값이 NULL 이면 클립보드에서를 가져옵니다 `COleDataObject` .

*pParentWnd*<br/>
대화 상자 개체가 속한 부모 또는 소유자 창 개체 (형식 `CWnd` )를 가리킵니다. NULL 인 경우에는 대화 상자의 부모 창이 주 응용 프로그램 창으로 설정 됩니다.

### <a name="remarks"></a>설명

이 함수는 개체를 생성 `COlePasteSpecialDialog` 합니다. 대화 상자를 표시 하려면 [DoModal](#domodal) 함수를 호출 합니다.

자세한 내용은 Windows SDK에서 [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) 열거 형식을 참조 하십시오.

## <a name="colepastespecialdialogcreateitem"></a><a name="createitem"></a> COlePasteSpecialDialog:: CreateItem

선택 하 여 붙여넣기 대화 상자에서 선택한 새 항목을 만듭니다.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>매개 변수

*pNewItem*<br/>
는 인스턴스를 가리킵니다 `COleClientItem` . NULL이 될 수 없습니다.

### <a name="return-value"></a>반환 값

항목이 성공적으로 만들어진 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[DoModal](#domodal) 가 IDOK를 반환한 후에만이 함수를 호출 해야 합니다.

## <a name="colepastespecialdialogdomodal"></a><a name="domodal"></a> COlePasteSpecialDialog::D oModal

OLE 붙여넣기 옵션 대화 상자를 표시 합니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

대화 상자의 완료 상태입니다. 다음 값 중 하나입니다.

- 대화 상자가 성공적으로 표시 되 면 IDOK입니다.

- 사용자가 대화 상자를 취소 한 경우 IDCANCEL입니다.

- 오류가 발생 한 경우 IDABORT입니다. IDABORT가 반환 되는 경우 `COleDialog::GetLastError` 멤버 함수를 호출 하 여 발생 한 오류 유형에 대 한 자세한 정보를 얻습니다. 가능한 오류 목록은 Windows SDK에서 [OleUIPasteSpecial](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw) 함수를 참조 하세요.

### <a name="remarks"></a>설명

[M_ps](#m_ps) 구조의 멤버를 설정 하 여 다양 한 대화 상자 컨트롤을 초기화 하려면를 호출 하기 전에이 작업을 수행 해야 합니다 `DoModal` . 대화 상자 개체가 생성 된 후에는이 작업을 수행 해야 합니다.

`DoModal`에서 IDOK를 반환 하는 경우 다른 멤버 함수를 호출 하 여 사용자가 대화 상자에 입력 한 설정 또는 정보를 검색할 수 있습니다.

## <a name="colepastespecialdialoggetdrawaspect"></a><a name="getdrawaspect"></a> COlePasteSpecialDialog:: GetDrawAspect

사용자가 선택한 항목을 아이콘으로 표시할지 여부를 결정 합니다.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>반환 값

개체를 렌더링 하는 데 필요한 메서드입니다.

- 대화 상자를 닫을 때 아이콘으로 표시 확인란을 선택 하지 않은 경우 DVASPECT_CONTENT 반환 됩니다.

- 대화 상자를 닫을 때 아이콘으로 표시 확인란을 선택 하면 DVASPECT_ICON 반환 됩니다.

### <a name="remarks"></a>설명

[DoModal](#domodal) 가 IDOK를 반환한 후에만이 함수를 호출 합니다.

모양 그리기에 대 한 자세한 내용은 Windows SDK의 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조를 참조 하세요.

## <a name="colepastespecialdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a> COlePasteSpecialDialog:: GetIconicMetafile 파일

사용자가 선택한 항목과 연결 된 메타 파일을 가져옵니다.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>반환 값

**확인** 을 선택 하 여 대화 상자를 닫을 때 아이콘으로 표시 확인란이 선택 된 경우 선택한 항목의 아이콘 측면을 포함 하는 메타 파일의 핸들입니다. 그렇지 않으면 NULL입니다.

## <a name="colepastespecialdialoggetpasteindex"></a><a name="getpasteindex"></a> COlePasteSpecialDialog::GetPasteIndex

사용자가 선택한 항목에 연결 된 인덱스 값을 가져옵니다.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>반환 값

사용자가 선택한 구조체의 배열에 대 한 인덱스입니다 `OLEUIPASTEENTRY` . 선택한 인덱스에 해당 하는 형식은 붙여넣기 작업을 수행할 때 사용 해야 합니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK [OLEUIPASTEENTRY](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw) 구조체를 참조 하세요.

## <a name="colepastespecialdialoggetselectiontype"></a><a name="getselectiontype"></a> COlePasteSpecialDialog:: GetSelectionType

사용자가 선택한 종류의 유형을 결정 합니다.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>반환 값

선택 된의 유형을 반환 합니다.

### <a name="remarks"></a>설명

반환 형식 값은 `Selection` 클래스에 선언 된 열거형 형식에 의해 지정 됩니다 `COlePasteSpecialDialog` .

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

이러한 값의 간략 한 desccriptions은 다음과 같습니다.

- `COlePasteSpecialDialog::pasteLink` 링크 붙여넣기 라디오 단추가 선택 되어 있고 선택한 형식이 표준 OLE 형식 이었습니다.

- `COlePasteSpecialDialog::pasteNormal` 붙여넣기 라디오 단추가 선택 되어 있고 선택한 형식은 표준 OLE 형식 이었습니다.

- `COlePasteSpecialDialog::pasteOther` 선택한 형식은 표준 OLE 형식이 아닙니다.

- `COlePasteSpecialDialog::pasteStatic` 선택한 형식은 메타 파일입니다.

## <a name="colepastespecialdialogm_ps"></a><a name="m_ps"></a> COlePasteSpecialDialog:: m_ps

특수 하 게 붙여넣기 대화 상자의 동작을 제어 하는 데 사용 되는 OLEUIPASTESPECIAL 형식의 구조입니다.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>설명

이 구조체의 멤버는 직접 또는 멤버 함수를 통해 수정할 수 있습니다.

자세한 내용은 Windows SDK [OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) 구조체를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 클래스](../../mfc/reference/coledialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 클래스](../../mfc/reference/coledialog-class.md)
