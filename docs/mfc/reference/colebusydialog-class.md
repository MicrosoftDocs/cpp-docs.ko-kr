---
description: '자세히 알아보기: COleBusyDialog 클래스'
title: COleBusyDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
ms.openlocfilehash: 7191cf193fccbe0883c8c888f888df94e1f70a23
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340933"
---
# <a name="colebusydialog-class"></a>COleBusyDialog 클래스

OLE 서버가 응답하지 않음 또는 서버가 사용 중임 대화 상자에 사용합니다.

## <a name="syntax"></a>구문

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|`COleBusyDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleBusyDialog::D oModal](#domodal)|OLE 서버 사용 중 대화 상자를 표시 합니다.|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|대화 상자에서 선택 하는 내용을 결정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|대화 상자의 동작을 제어 하는 OLEUIBUSY 형식의 구조입니다.|

## <a name="remarks"></a>설명

`COleBusyDialog`이러한 대화 상자를 호출 하려면 클래스의 개체를 만듭니다. `COleBusyDialog` 개체를 생성한 후에는 [m_bz](#m_bz) 구조를 사용하여 대화 상자에서 컨트롤의 값 또는 상태를 초기화할 수 있습니다. `m_bz`구조는 OLEUIBUSY 형식입니다. 이 대화 상자 클래스를 사용 하는 방법에 대 한 자세한 내용은 [DoModal](#domodal) 멤버 함수를 참조 하세요.

> [!NOTE]
> 응용 프로그램 마법사에서 생성 된 컨테이너 코드는이 클래스를 사용 합니다.

자세한 내용은 Windows SDK [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) 구조체를 참조 하세요.

OLE 관련 대화 상자에 대 한 자세한 내용은 [ole의 아티클 대화 상자](../../mfc/dialog-boxes-in-ole.md)를 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxodlgs

## <a name="colebusydialogcolebusydialog"></a><a name="colebusydialog"></a> COleBusyDialog::COleBusyDialog

이 함수는 개체를 생성 `COleBusyDialog` 합니다.

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*htaskBusy*<br/>
사용 중인 서버 작업에 대 한 핸들입니다.

*bNotResponding*<br/>
TRUE 이면 서버 사용 중 대화 상자 대신 응답 하지 않음 대화 상자를 호출 합니다. 응답 없음 대화 상자의 표현은 서버 사용 중 대화 상자의 단어와 약간 다르며 취소 단추를 사용할 수 없습니다.

*dwFlags*<br/>
만들기 플래그입니다. 비트 or 연산자와 결합 된 다음 값을 0 개 이상 포함할 수 있습니다.

- 대화 상자를 호출할 때 취소 단추를 사용 하지 않도록 설정 BZ_DISABLECANCELBUTTON 합니다.

- 대화 상자를 호출할 때 전환 단추를 사용 하지 않도록 설정 BZ_DISABLESWITCHTOBUTTON 합니다.

- 대화 상자를 호출할 때 다시 시도 단추를 사용 하지 않도록 설정 BZ_DISABLERETRYBUTTON 합니다.

*pParentWnd*<br/>
대화 상자 개체가 속한 부모 또는 소유자 창 개체 (형식 `CWnd` )를 가리킵니다. NULL 인 경우에는 대화 상자 개체의 부모 창이 주 응용 프로그램 창으로 설정 됩니다.

### <a name="remarks"></a>설명

대화 상자를 표시 하려면 [DoModal](#domodal)를 호출 합니다.

자세한 내용은 Windows SDK [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) 구조체를 참조 하세요.

## <a name="colebusydialogdomodal"></a><a name="domodal"></a> COleBusyDialog::D oModal

이 함수를 호출 하 여 OLE 서버 사용 중 또는 서버가 응답 하지 않음 대화 상자를 표시 합니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

대화 상자의 완료 상태입니다. 다음 값 중 하나입니다.

- 대화 상자가 성공적으로 표시 되 면 IDOK입니다.

- 사용자가 대화 상자를 취소 한 경우 IDCANCEL입니다.

- 오류가 발생 한 경우 IDABORT입니다. IDABORT가 반환 되는 경우 `COleDialog::GetLastError` 멤버 함수를 호출 하 여 발생 한 오류 유형에 대 한 자세한 정보를 얻습니다. 가능한 오류 목록은 Windows SDK에서 [OleUIBusy](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw) 함수를 참조 하세요.

### <a name="remarks"></a>설명

[M_bz](#m_bz) 구조의 멤버를 설정 하 여 다양 한 대화 상자 컨트롤을 초기화 하려면를 호출 하기 전에이 작업을 수행 해야 합니다 `DoModal` . 대화 상자 개체가 생성 된 후에는이 작업을 수행 해야 합니다.

`DoModal`에서 IDOK를 반환 하는 경우 다른 멤버 함수를 호출 하 여 대화 상자에 사용자가 입력 한 설정이 나 정보를 검색할 수 있습니다.

## <a name="colebusydialoggetselectiontype"></a><a name="getselectiontype"></a> COleBusyDialog:: GetSelectionType

서버 사용 중 대화 상자에서 사용자가 선택한 선택 유형을 가져오려면이 함수를 호출 합니다.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>반환 값

선택 항목의 유형입니다.

### <a name="remarks"></a>설명

반환 형식 값은 `Selection` 클래스에 선언 된 열거형 형식에 의해 지정 됩니다 `COleBusyDialog` .

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

이러한 값에 대 한 간략 한 설명은 다음과 같습니다.

- `COleBusyDialog::switchTo` 전환 단추를 눌렀습니다.

- `COleBusyDialog::retry` 다시 시도 단추를 눌렀습니다.

- `COleBusyDialog::callUnblocked` 서버를 활성화 하는 호출은 이제 차단이 해제 됩니다.

## <a name="colebusydialogm_bz"></a><a name="m_bz"></a> COleBusyDialog:: m_bz

서버 사용 중 대화 상자의 동작을 제어 하는 데 사용 되는 OLEUIBUSY 형식의 구조입니다.

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>설명

이 구조체의 멤버는 직접 또는 멤버 함수를 통해 수정할 수 있습니다.

자세한 내용은 Windows SDK [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) 구조체를 참조 하세요.

## <a name="see-also"></a>참고 항목

[COleDialog 클래스](../../mfc/reference/coledialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 클래스](../../mfc/reference/coledialog-class.md)
