---
description: '자세히 알아보기: COleChangeSourceDialog 클래스'
title: COleChangeSourceDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::DoModal
- AFXODLGS/COleChangeSourceDialog::GetDisplayName
- AFXODLGS/COleChangeSourceDialog::GetFileName
- AFXODLGS/COleChangeSourceDialog::GetFromPrefix
- AFXODLGS/COleChangeSourceDialog::GetItemName
- AFXODLGS/COleChangeSourceDialog::GetToPrefix
- AFXODLGS/COleChangeSourceDialog::IsValidSource
- AFXODLGS/COleChangeSourceDialog::m_cs
helpviewer_keywords:
- COleChangeSourceDialog [MFC], COleChangeSourceDialog
- COleChangeSourceDialog [MFC], DoModal
- COleChangeSourceDialog [MFC], GetDisplayName
- COleChangeSourceDialog [MFC], GetFileName
- COleChangeSourceDialog [MFC], GetFromPrefix
- COleChangeSourceDialog [MFC], GetItemName
- COleChangeSourceDialog [MFC], GetToPrefix
- COleChangeSourceDialog [MFC], IsValidSource
- COleChangeSourceDialog [MFC], m_cs
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
ms.openlocfilehash: 2962534b5c1e85e274d134a347821a94d646b66d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209934"
---
# <a name="colechangesourcedialog-class"></a>COleChangeSourceDialog 클래스

OLE 소스 변경 대화 상자에 사용합니다.

## <a name="syntax"></a>구문

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|`COleChangeSourceDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleChangeSourceDialog::D oModal](#domodal)|OLE 소스 변경 대화 상자를 표시 합니다.|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|전체 소스 표시 이름을 가져옵니다.|
|[COleChangeSourceDialog::GetFileName](#getfilename)|원본 이름에서 파일 이름을 가져옵니다.|
|[COleChangeSourceDialog:: GetFromPrefix](#getfromprefix)|이전 소스의 접두사를 가져옵니다.|
|[COleChangeSourceDialog::GetItemName](#getitemname)|원본 이름에서 항목 이름을 가져옵니다.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|새 소스의 접두사를 가져옵니다.|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|소스가 유효한 지 여부를 나타냅니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[COleChangeSourceDialog:: m_cs](#m_cs)|대화 상자의 동작을 제어 하는 구조체입니다.|

## <a name="remarks"></a>설명

`COleChangeSourceDialog`이 대화 상자를 호출 하려면 클래스의 개체를 만듭니다. `COleChangeSourceDialog` 개체를 생성한 후에는 [m_cs](#m_cs) 구조를 사용하여 대화 상자에서 컨트롤의 값 또는 상태를 초기화할 수 있습니다. `m_cs`구조는 [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)형식입니다. 이 대화 상자 클래스를 사용 하는 방법에 대 한 자세한 내용은 [DoModal](#domodal) 멤버 함수를 참조 하세요.

자세한 내용은 Windows SDK의 [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) 구조를 참조 하세요.

OLE 관련 대화 상자에 대 한 자세한 내용은 [ole의 아티클 대화 상자](../../mfc/dialog-boxes-in-ole.md)를 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxodlgs

## <a name="colechangesourcedialogcolechangesourcedialog"></a><a name="colechangesourcedialog"></a> COleChangeSourceDialog::COleChangeSourceDialog

이 함수는 개체를 생성 `COleChangeSourceDialog` 합니다.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*pItem*<br/>
원본을 업데이트할 연결 된 [COleClientItem](../../mfc/reference/coleclientitem-class.md) 에 대 한 포인터입니다.

*pParentWnd*<br/>
대화 상자 개체가 속한 부모 또는 소유자 창 개체 (형식 `CWnd` )를 가리킵니다. NULL 이면 대화 상자의 부모 창이 주 응용 프로그램 창으로 설정 됩니다.

### <a name="remarks"></a>설명

대화 상자를 표시 하려면 [DoModal](#domodal) 함수를 호출 합니다.

자세한 내용은 Windows SDK에서 [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) Structure and [OLEUICHANGESOURCE](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) 함수를 참조 하세요.

## <a name="colechangesourcedialogdomodal"></a><a name="domodal"></a> COleChangeSourceDialog::D oModal

이 함수를 호출 하 여 OLE 소스 변경 대화 상자를 표시 합니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

대화 상자의 완료 상태입니다. 다음 값 중 하나입니다.

- 대화 상자가 성공적으로 표시 되 면 IDOK입니다.

- 사용자가 대화 상자를 취소 한 경우 IDCANCEL입니다.

- 오류가 발생 한 경우 IDABORT입니다. IDABORT가 반환 되 면 [Coledialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) 멤버 함수를 호출 하 여 발생 한 오류 유형에 대 한 자세한 정보를 가져옵니다. 가능한 오류 목록은 Windows SDK에서 [OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) 함수를 참조 하세요.

### <a name="remarks"></a>설명

[M_cs](#m_cs) 구조의 멤버를 설정 하 여 다양 한 대화 상자 컨트롤을 초기화 하려면를 호출 하기 전에이 작업을 수행 해야 합니다 `DoModal` . 대화 상자 개체가 생성 된 후에는이 작업을 수행 해야 합니다.

`DoModal`에서 IDOK를 반환 하는 경우 멤버 함수를 호출 하 여 대화 상자에서 사용자가 입력 한 설정이 나 정보를 검색할 수 있습니다. 다음 목록에서는 일반적인 쿼리 함수에 대해 이름을 표시 합니다.

- [GetFileName](#getfilename)

- [GetDisplayName](#getdisplayname)

- [GetItemName](#getitemname)

## <a name="colechangesourcedialoggetdisplayname"></a><a name="getdisplayname"></a> COleChangeSourceDialog:: GetDisplayName

연결 된 클라이언트 항목의 전체 표시 이름을 검색 하려면이 함수를 호출 합니다.

```
CString GetDisplayName();
```

### <a name="return-value"></a>반환 값

생성자에 지정 된 [COleClientItem](../../mfc/reference/coleclientitem-class.md) 의 전체 소스 표시 이름 (모니커)입니다.

## <a name="colechangesourcedialoggetfilename"></a><a name="getfilename"></a> COleChangeSourceDialog:: GetFileName

이 함수를 호출 하 여 연결 된 클라이언트 항목에 대 한 표시 이름의 파일 모니커 부분을 검색 합니다.

```
CString GetFileName();
```

### <a name="return-value"></a>반환 값

생성자에 지정 된 [COleClientItem](../../mfc/reference/coleclientitem-class.md) 에 대 한 소스 표시 이름의 파일 모니커 부분입니다.

### <a name="remarks"></a>설명

항목 모니커와 함께 파일 모니커는 전체 표시 이름을 제공 합니다.

## <a name="colechangesourcedialoggetfromprefix"></a><a name="getfromprefix"></a> COleChangeSourceDialog:: GetFromPrefix

이 함수를 호출 하 여 소스에 대 한 이전 접두사 문자열을 가져옵니다.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>반환 값

소스의 이전 접두사 문자열입니다.

### <a name="remarks"></a>설명

[DoModal](#domodal) 가 IDOK를 반환한 후에만이 함수를 호출 합니다.

이 값 `lpszFrom` 은 [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) 구조체의 멤버에서 직접 가져옵니다.

자세한 내용은 Windows SDK의 [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) 구조를 참조 하세요.

## <a name="colechangesourcedialoggetitemname"></a><a name="getitemname"></a> COleChangeSourceDialog:: GetItemName

이 함수를 호출 하 여 연결 된 클라이언트 항목에 대 한 표시 이름의 항목 모니커 부분을 검색 합니다.

```
CString GetItemName();
```

### <a name="return-value"></a>반환 값

생성자에 지정 된 [COleClientItem](../../mfc/reference/coleclientitem-class.md) 에 대 한 소스 표시 이름의 항목 모니커 부분입니다.

### <a name="remarks"></a>설명

항목 모니커와 함께 파일 모니커는 전체 표시 이름을 제공 합니다.

## <a name="colechangesourcedialoggettoprefix"></a><a name="gettoprefix"></a> COleChangeSourceDialog::GetToPrefix

이 함수를 호출 하 여 소스에 대 한 새 접두사 문자열을 가져옵니다.

```
CString GetToPrefix();
```

### <a name="return-value"></a>반환 값

소스의 새 접두사 문자열입니다.

### <a name="remarks"></a>설명

[DoModal](#domodal) 가 IDOK를 반환한 후에만이 함수를 호출 합니다.

이 값 `lpszTo` 은 [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) 구조체의 멤버에서 직접 가져옵니다.

자세한 내용은 Windows SDK의 [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) 구조를 참조 하세요.

## <a name="colechangesourcedialogm_cs"></a><a name="m_cs"></a> COleChangeSourceDialog:: m_cs

이 데이터 멤버는 [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)형식의 구조입니다.

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>설명

`OLEUICHANGESOURCE` 는 OLE 원본 변경 대화 상자의 동작을 제어 하는 데 사용 됩니다. 이 구조체의 멤버를 직접 수정할 수 있습니다.

자세한 내용은 Windows SDK의 [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) 구조를 참조 하세요.

## <a name="colechangesourcedialogisvalidsource"></a><a name="isvalidsource"></a> COleChangeSourceDialog:: Is유효한 원본

새 소스가 유효한 지 여부를 확인 하려면이 함수를 호출 합니다.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>반환 값

새 소스가 올바르면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[DoModal](#domodal) 가 IDOK를 반환한 후에만이 함수를 호출 합니다.

자세한 내용은 Windows SDK의 [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) 구조를 참조 하세요.

## <a name="see-also"></a>참고 항목

[COleDialog 클래스](../../mfc/reference/coledialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 클래스](../../mfc/reference/coledialog-class.md)
