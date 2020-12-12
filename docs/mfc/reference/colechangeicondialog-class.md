---
description: '자세히 알아보기: COleChangeIconDialog 클래스'
title: COleChangeIconDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
ms.openlocfilehash: 5ec6113bbcf63462380f18c4ac52abbb8706c8d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209960"
---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog 클래스

OLE 아이콘 변경 대화 상자에 사용합니다.

## <a name="syntax"></a>구문

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|`COleChangeIconDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleChangeIconDialog::D oChangeIcon](#dochangeicon)|대화 상자에 지정 된 변경을 수행 합니다.|
|[COleChangeIconDialog::DoModal](#domodal)|OLE 2 아이콘 변경 대화 상자를 표시 합니다.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|이 항목의 아이콘 폼과 연결 된 메타 파일에 대 한 핸들을 가져옵니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|대화 상자의 동작을 제어 하는 구조체입니다.|

## <a name="remarks"></a>설명

`COleChangeIconDialog`이 대화 상자를 호출 하려면 클래스의 개체를 만듭니다. `COleChangeIconDialog` 개체를 생성한 후에는 [m_ci](#m_ci) 구조를 사용하여 대화 상자에서 컨트롤의 값 또는 상태를 초기화할 수 있습니다. `m_ci`구조는 OLEUICHANGEICON 형식입니다. 이 대화 상자 클래스를 사용 하는 방법에 대 한 자세한 내용은 [DoModal](#domodal) 멤버 함수를 참조 하세요.

자세한 내용은 Windows SDK [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) 구조체를 참조 하세요.

OLE 관련 대화 상자에 대 한 자세한 내용은 [ole의 아티클 대화 상자](../../mfc/dialog-boxes-in-ole.md)를 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxodlgs

## <a name="colechangeicondialogcolechangeicondialog"></a><a name="colechangeicondialog"></a> COleChangeIconDialog::COleChangeIconDialog

이 함수는 개체만 생성 `COleChangeIconDialog` 합니다.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*pItem*<br/>
변환할 항목을 가리킵니다.

*dwFlags*<br/>
비트 or 연산자를 사용 하 여 결합 된 다음 값을 포함 하는 생성 플래그입니다.

- CIF_SELECTCURRENT 대화 상자를 호출할 때 현재 라디오 단추를 처음 선택 하도록 지정 합니다. 이것이 기본값입니다.

- CIF_SELECTDEFAULT 대화 상자를 호출할 때 기본 라디오 단추가 처음에 선택 되도록 지정 합니다.

- CIF_SELECTFROMFILE 대화 상자를 호출할 때 파일에서 라디오 단추를 처음으로 선택 하도록 지정 합니다.

- CIF_SHOWHELP 대화 상자를 호출할 때 도움말 단추가 표시 되도록 지정 합니다.

- CIF_USEICONEXE은 `szIconExe` 형식에서 검색 하는 대신 [m_ci](#m_ci) 의 필드에 지정 된 실행 파일에서 아이콘을 추출 하도록 지정 합니다. 이는 비 OLE 파일을 포함 하거나 연결 하는 데 유용 합니다.

*pParentWnd*<br/>
대화 상자 개체가 속한 부모 또는 소유자 창 개체 (형식 `CWnd` )를 가리킵니다. NULL 이면 대화 상자의 부모 창이 주 응용 프로그램 창으로 설정 됩니다.

### <a name="remarks"></a>설명

대화 상자를 표시 하려면 [DoModal](#domodal) 함수를 호출 합니다.

자세한 내용은 Windows SDK [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) 구조체를 참조 하세요.

## <a name="colechangeicondialogdochangeicon"></a><a name="dochangeicon"></a> COleChangeIconDialog::D oChangeIcon

[DoModal](#domodal) 가 IDOK를 반환한 후이 함수를 호출 하 여 대화 상자에서 선택한 항목에 대 한 항목을 나타내는 아이콘을 변경 합니다.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>매개 변수

*pItem*<br/>
아이콘이 변경 되 고 있는 항목을 가리킵니다.

### <a name="return-value"></a>반환 값

변경이 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="colechangeicondialogdomodal"></a><a name="domodal"></a> COleChangeIconDialog::D oModal

이 함수를 호출 하 여 OLE 아이콘 변경 대화 상자를 표시 합니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

대화 상자의 완료 상태입니다. 다음 값 중 하나입니다.

- 대화 상자가 성공적으로 표시 되 면 IDOK입니다.

- 사용자가 대화 상자를 취소 한 경우 IDCANCEL입니다.

- 오류가 발생 한 경우 IDABORT입니다. IDABORT가 반환 되는 경우 `COleDialog::GetLastError` 멤버 함수를 호출 하 여 발생 한 오류 유형에 대 한 자세한 정보를 얻습니다. 가능한 오류 목록은 Windows SDK에서 [OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw) 함수를 참조 하세요.

### <a name="remarks"></a>설명

[M_ci](#m_ci) 구조의 멤버를 설정 하 여 다양 한 대화 상자 컨트롤을 초기화 하려면를 호출 하기 전에이 작업을 수행 해야 합니다 `DoModal` . 대화 상자 개체가 생성 된 후에는이 작업을 수행 해야 합니다.

`DoModal`에서 IDOK를 반환 하는 경우 다른 멤버 함수를 호출 하 여 대화 상자에 사용자가 입력 한 설정이 나 정보를 검색할 수 있습니다.

## <a name="colechangeicondialoggeticonicmetafile"></a><a name="geticonicmetafile"></a> COleChangeIconDialog:: GetIconicMetafile 파일

이 함수를 호출 하 여 선택한 항목의 아이콘 측면을 포함 하는 메타 파일에 대 한 핸들을 가져옵니다.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>반환 값

**확인** 을 선택 하 여 대화 상자를 해제 한 경우 새 아이콘의 아이콘 측면을 포함 하는 메타 파일에 대 한 핸들입니다. 그렇지 않으면 대화 상자를 표시 하기 전의 아이콘이 표시 됩니다.

## <a name="colechangeicondialogm_ci"></a><a name="m_ci"></a> COleChangeIconDialog:: m_ci

아이콘 변경 대화 상자의 동작을 제어 하는 데 사용 되는 OLEUICHANGEICON 형식의 구조입니다.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>설명

이 구조체의 멤버는 직접 또는 멤버 함수를 통해 수정할 수 있습니다.

자세한 내용은 Windows SDK [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) 구조체를 참조 하세요.

## <a name="see-also"></a>참고 항목

[COleDialog 클래스](../../mfc/reference/coledialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 클래스](../../mfc/reference/coledialog-class.md)
