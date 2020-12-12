---
description: '자세히 알아보기: COleInsertDialog 클래스'
title: COleInsertDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
ms.openlocfilehash: 54cd2f372ae43739a94bf03f8a432c52c914e5ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227041"
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog 클래스

OLE 개체 삽입 대화 상자에 사용합니다.

## <a name="syntax"></a>구문

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleInsertDialog:: COleInsertDialog](#coleinsertdialog)|`COleInsertDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|대화 상자에서 선택한 항목을 만듭니다.|
|[COleInsertDialog::DoModal](#domodal)|OLE 개체 삽입 대화 상자를 표시 합니다.|
|[COleInsertDialog::GetClassID](#getclassid)|선택 된 항목과 연결 된 CLSID를 가져옵니다.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|항목을 아이콘으로 그릴지 여부를 나타냅니다.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|이 항목의 아이콘 폼과 연결 된 메타 파일에 대 한 핸들을 가져옵니다.|
|[COleInsertDialog::GetPathName](#getpathname)|대화 상자에서 선택한 파일의 전체 경로를 가져옵니다.|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|선택한 개체의 형식을 가져옵니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|대화 상자의 동작을 제어 하는 OLEUIINSERTOBJECT 형식의 구조체입니다.|

## <a name="remarks"></a>설명

`COleInsertDialog`이 대화 상자를 호출 하려면 클래스의 개체를 만듭니다. `COleInsertDialog` 개체를 생성한 후에는 [m_io](#m_io) 구조를 사용하여 대화 상자에서 컨트롤의 값 또는 상태를 초기화할 수 있습니다. `m_io`구조는 OLEUIINSERTOBJECT 형식입니다. 이 대화 상자 클래스를 사용 하는 방법에 대 한 자세한 내용은 [DoModal](#domodal) 멤버 함수를 참조 하세요.

> [!NOTE]
> 응용 프로그램 마법사에서 생성 된 컨테이너 코드는이 클래스를 사용 합니다.

자세한 내용은 Windows SDK [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) 구조체를 참조 하세요.

OLE 관련 대화 상자에 대 한 자세한 내용은 [ole의 아티클 대화 상자](../../mfc/dialog-boxes-in-ole.md)를 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxodlgs

## <a name="coleinsertdialogcoleinsertdialog"></a><a name="coleinsertdialog"></a> COleInsertDialog:: COleInsertDialog

이 함수는 개체만 생성 `COleInsertDialog` 합니다.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*dwFlags*<br/>
비트 or 연산자를 사용 하 여 결합할 다음 값의 개수가 포함 된 생성 플래그입니다.

- IOF_SHOWHELP 대화 상자를 호출할 때 도움말 단추가 표시 되도록 지정 합니다.

- IOF_SELECTCREATENEW 대화 상자를 호출할 때 새로 만들기 라디오 단추를 처음으로 선택 하도록 지정 합니다. 이것은 기본값이 며 IOF_SELECTCREATEFROMFILE와 함께 사용할 수 없습니다.

- IOF_SELECTCREATEFROMFILE 대화 상자를 호출할 때 파일에서 만들기 라디오 단추가 처음에 선택 되도록 지정 합니다. IOF_SELECTCREATENEW와 함께 사용할 수 없습니다.

- IOF_CHECKLINK 대화 상자를 호출할 때 링크 확인란을 처음에 선택 하도록 지정 합니다.

- IOF_DISABLELINK 대화 상자를 호출할 때 링크 확인란을 사용 하지 않도록 지정 합니다.

- IOF_CHECKDISPLAYASICON 아이콘으로 표시 확인란을 처음에 선택 하 고, 현재 아이콘을 표시 하 고, 대화 상자를 호출할 때 아이콘 변경 단추를 사용할 수 있도록 지정 합니다.

- IOF_VERIFYSERVERSEXIST는 대화 상자가 등록 데이터베이스에 지정 된 서버가 대화 상자가 표시 되기 전에 존재 하는지 확인 하 여 목록 상자에 추가 하는 클래스의 유효성을 검사 하도록 지정 합니다. 이 플래그를 설정 하면 성능이 상당히 저하 될 수 있습니다.

*pParentWnd*<br/>
대화 상자 개체가 속한 부모 또는 소유자 창 개체 (형식 `CWnd` )를 가리킵니다. NULL 인 경우에는 대화 상자 개체의 부모 창이 주 응용 프로그램 창으로 설정 됩니다.

### <a name="remarks"></a>설명

대화 상자를 표시 하려면 [DoModal](#domodal) 함수를 호출 합니다.

## <a name="coleinsertdialogcreateitem"></a><a name="createitem"></a> COleInsertDialog:: CreateItem

[DoModal](#domodal) 가 IDOK를 반환 하는 경우에만이 함수를 호출 하 여 [COleClientItem](../../mfc/reference/coleclientitem-class.md) 형식의 개체를 만듭니다.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>매개 변수

*pItem*<br/>
만들 항목을 가리킵니다.

### <a name="return-value"></a>반환 값

항목이 만들어진 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`COleClientItem`이 함수를 호출 하려면 먼저 개체를 할당 해야 합니다.

## <a name="coleinsertdialogdomodal"></a><a name="domodal"></a> COleInsertDialog::D oModal

OLE 개체 삽입 대화 상자를 표시 하려면이 함수를 호출 합니다.

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>매개 변수

*dwFlags*<br/>
다음 값 중 하나입니다.

`COleInsertDialog::DocObjectsOnly` DocObjects만 삽입 합니다.

`COleInsertDialog::ControlsOnly` ActiveX 컨트롤만 삽입 합니다.

0은 DocObject 및 ActiveX 컨트롤을 삽입 하지 않습니다. 이 값은 위에 나열 된 첫 번째 프로토타입과 동일한 구현을 생성 합니다.

### <a name="return-value"></a>반환 값

대화 상자의 완료 상태입니다. 다음 값 중 하나입니다.

- 대화 상자가 성공적으로 표시 되 면 IDOK입니다.

- 사용자가 대화 상자를 취소 한 경우 IDCANCEL입니다.

- 오류가 발생 한 경우 IDABORT입니다. IDABORT가 반환 되 면 [Coledialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) 멤버 함수를 호출 하 여 발생 한 오류 유형에 대 한 자세한 정보를 가져옵니다. 가능한 오류 목록은 Windows SDK에서 [OleUIInsertObject](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw) 함수를 참조 하세요.

### <a name="remarks"></a>설명

[M_io](#m_io) 구조의 멤버를 설정 하 여 다양 한 대화 상자 컨트롤을 초기화 하려면를 호출 하기 전에이 작업을 수행 해야 합니다 `DoModal` . 대화 상자 개체가 생성 된 후에는이 작업을 수행 해야 합니다.

에서 `DoModal` IDOK를 반환 하는 경우 다른 멤버 함수를 호출 하 여 사용자가 대화 상자에 설정 또는 정보 입력을 검색할 수 있습니다.

## <a name="coleinsertdialoggetclassid"></a><a name="getclassid"></a> COleInsertDialog:: GetClassID

[DoModal](#domodal) 이 IDOK를 반환 하 고 선택 형식이 인 경우에만이 함수를 호출 하 여 선택한 항목과 연결 된 CLSID를 가져옵니다 `COleInsertDialog::createNewItem` .

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>반환 값

선택한 항목과 연결 된 CLSID를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK의 [CLSID 키](/windows/win32/com/clsid-key-hklm) 를 참조 하세요.

## <a name="coleinsertdialoggetdrawaspect"></a><a name="getdrawaspect"></a> COleInsertDialog:: GetDrawAspect

사용자가 선택한 항목을 아이콘으로 표시 하도록 선택 했는지 여부를 확인 하려면이 함수를 호출 합니다.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>반환 값

개체를 렌더링 하는 데 필요한 메서드입니다.

- 아이콘으로 표시 확인란을 선택 하지 않은 경우 DVASPECT_CONTENT 반환 됩니다.

- 아이콘으로 표시 확인란을 선택 하면 DVASPECT_ICON 반환 됩니다.

### <a name="remarks"></a>설명

[DoModal](#domodal) 이 IDOK를 반환 하는 경우에만이 함수를 호출 합니다.

모양 그리기에 대 한 자세한 내용은 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) data structure in the Windows SDK를 참조 하세요.

## <a name="coleinsertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a> COleInsertDialog:: GetIconicMetafile 파일

이 함수를 호출 하 여 선택한 항목의 아이콘 측면을 포함 하는 메타 파일에 대 한 핸들을 가져옵니다.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>반환 값

**확인** 을 선택 하 여 대화 상자를 닫을 때 아이콘으로 표시 확인란이 선택 된 경우 선택한 항목의 아이콘 측면을 포함 하는 메타 파일에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

## <a name="coleinsertdialoggetpathname"></a><a name="getpathname"></a> COleInsertDialog:: GetPathName

[DoModal](#domodal) 이 IDOK를 반환 하 고 선택 형식이가 아닌 경우에만 선택한 파일의 전체 경로를 가져오려면이 함수를 호출 `COleInsertDialog::createNewItem` 합니다.

```
CString GetPathName() const;
```

### <a name="return-value"></a>반환 값

대화 상자에서 선택한 파일의 전체 경로입니다. 선택 유형이 인 경우 `createNewItem` 이 함수는 `CString` 릴리스 모드에서 의미가 없는을 반환 하거나 디버그 모드에서 어설션을 발생 시킵니다.

## <a name="coleinsertdialoggetselectiontype"></a><a name="getselectiontype"></a> COleInsertDialog:: GetSelectionType

**확인** 을 선택 하 여 개체 삽입 대화 상자를 닫을 때 선택한 선택 유형을 가져오려면이 함수를 호출 합니다.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>반환 값

선택 항목의 유형입니다.

### <a name="remarks"></a>설명

반환 형식 값은 `Selection` 클래스에 선언 된 열거형 형식에 의해 지정 됩니다 `COleInsertDialog` .

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

이러한 값에 대 한 간략 한 설명은 다음과 같습니다.

- `COleInsertDialog::createNewItem` 새로 만들기 라디오 단추를 선택 했습니다.

- `COleInsertDialog::insertFromFile` 파일에서 만들기 라디오 단추가 선택 되었고 링크 확인란을 선택 하지 않았습니다.

- `COleInsertDialog::linkToFile` 파일에서 만들기 라디오 단추가 선택 되었고 링크 확인란이 선택 되었습니다.

## <a name="coleinsertdialogm_io"></a><a name="m_io"></a> COleInsertDialog:: m_io

개체 삽입 대화 상자의 동작을 제어 하는 데 사용 되는 OLEUIINSERTOBJECT 형식의 구조입니다.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>설명

이 구조체의 멤버는 직접 또는 멤버 함수를 통해 수정할 수 있습니다.

자세한 내용은 Windows SDK [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) 구조체를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 클래스](../../mfc/reference/coledialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 클래스](../../mfc/reference/coledialog-class.md)
