---
description: '자세히 알아보기: CDataExchange 클래스'
title: CDataExchange 클래스
ms.date: 11/04/2016
f1_keywords:
- CDataExchange
- AFXWIN/CDataExchange
- AFXWIN/CDataExchange::CDataExchange
- AFXWIN/CDataExchange::Fail
- AFXWIN/CDataExchange::PrepareCtrl
- AFXWIN/CDataExchange::PrepareEditCtrl
- AFXWIN/CDataExchange::PrepareOleCtrl
- AFXWIN/CDataExchange::m_bSaveAndValidate
- AFXWIN/CDataExchange::m_pDlgWnd
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
ms.openlocfilehash: 36d11dc2b74142bd869b0e7b459d8bdb888b2cef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222179"
---
# <a name="cdataexchange-class"></a>CDataExchange 클래스

Microsoft Foundation 클래스에서 사용되는 DDX(대화 상자 데이터 교환) 및 DDV(대화 상자 데이터 유효성 검사) 루틴을 지원합니다.

## <a name="syntax"></a>구문

```
class CDataExchange
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDataExchange:: CDataExchange](#cdataexchange)|`CDataExchange` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDataExchange:: Fail](#fail)|유효성 검사에 실패 하면 호출 됩니다. 포커스를 이전 컨트롤로 다시 설정 하 고 예외를 throw 합니다.|
|[CDataExchange::P repareCtrl](#preparectrl)|데이터 교환 또는 유효성 검사를 위해 지정 된 컨트롤을 준비 합니다. 비 편집 컨트롤에는를 사용 합니다.|
|[CDataExchange::P repareEditCtrl](#prepareeditctrl)|데이터 교환 또는 유효성 검사를 위해 지정 된 편집 컨트롤을 준비 합니다.|
|[CDataExchange::P repareOleCtrl](#prepareolectrl)|데이터 교환 또는 유효성 검사를 위해 지정 된 OLE 컨트롤을 준비 합니다. 비 편집 컨트롤에는를 사용 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDataExchange:: m_bSaveAndValidate](#m_bsaveandvalidate)|DDX 및 DDV의 방향에 대 한 플래그입니다.|
|[CDataExchange:: m_pDlgWnd](#m_pdlgwnd)|데이터 교환이 이루어지는 대화 상자 또는 창입니다.|

## <a name="remarks"></a>설명

`CDataExchange` 에 기본 클래스가 없습니다.

사용자 지정 데이터 형식 또는 컨트롤에 대 한 데이터 교환 루틴을 작성 하는 경우 또는 사용자 고유의 데이터 유효성 검사 루틴을 작성 하는 경우이 클래스를 사용 합니다. 사용자 고유의 DDX 및 DDV 루틴을 작성 하는 방법에 대 한 자세한 내용은 [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md)을 참조 하십시오. DDX 및 DDV의 개요는 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md) 및 [대화 상자](../../mfc/dialog-boxes.md)를 참조 하세요.

`CDataExchange`개체는 DDX 및 DDV를 수행 하는 데 필요한 컨텍스트 정보를 제공 합니다. DDX를 사용 하 여 데이터 멤버의 대화 상자 컨트롤의 초기 값을 채우는 경우 플래그 *M_BSAVEANDVALIDATE* FALSE입니다. DDV를 사용 하 여 데이터 값의 유효성을 검사 하는 경우에는 DDX를 사용 하 여 대화 상자 컨트롤의 현재 값을 데이터 멤버로 설정 하는 플래그 *M_BSAVEANDVALIDATE* TRUE입니다. DDV 유효성 검사가 실패 하는 경우 DDV 프로시저는 입력 오류를 설명 하는 메시지 상자를 표시 합니다. DDV 프로시저는 `Fail` 를 호출 하 여 포커스를 잘못 된 컨트롤로 다시 설정 하 고 예외를 throw 하 여 유효성 검사 프로세스를 중지 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CDataExchange`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cdataexchangecdataexchange"></a><a name="cdataexchange"></a> CDataExchange:: CDataExchange

개체를 생성 하려면이 멤버 함수를 호출 `CDataExchange` 합니다.

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>매개 변수

*pDlgWnd*<br/>
컨트롤을 포함 하는 부모 창에 대 한 포인터입니다. 일반적으로이 개체는 [CDialog](../../mfc/reference/cdialog-class.md)파생 개체입니다.

*bSaveAndValidate*<br/>
TRUE 이면이 개체가 데이터의 유효성을 검사 한 다음 컨트롤의 데이터를 멤버에 씁니다. FALSE 이면이 개체가 멤버에서 컨트롤로 데이터를 이동 합니다.

### <a name="remarks"></a>설명

`CDataExchange`사용자 창의 [CWnd::D odataexchange](../../mfc/reference/cwnd-class.md#dodataexchange) 멤버 함수에 전달할 추가 정보를 데이터 교환 개체에 저장 하도록 직접 개체를 구성 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

## <a name="cdataexchangefail"></a><a name="fail"></a> CDataExchange:: Fail

DDV (대화 상자 데이터 유효성 검사) 작업이 실패할 경우 프레임 워크는이 멤버 함수를 호출 합니다.

```cpp
void Fail();
```

### <a name="remarks"></a>설명

`Fail` 유효성 검사에 실패 한 컨트롤 (복원할 컨트롤이 있는 경우)에 포커스 및 선택을 복원 합니다. `Fail` 그런 다음는 [Cuserexception](../../mfc/reference/cuserexception-class.md) 형식의 예외를 throw 하 여 유효성 검사 프로세스를 중지 합니다. 예외는 표시 되는 오류를 설명 하는 메시지 상자를 발생 시킵니다. DDV 유효성 검사에 실패 하면 사용자는 잘못 된 컨트롤에 데이터를 다시 입력할 수 있습니다.

구현자 사용자 지정 DDV 루틴은 `Fail` 유효성 검사가 실패할 경우 루틴에서 호출할 수 있습니다.

사용자 고유의 DDX 및 DDV 루틴을 작성 하는 방법에 대 한 자세한 내용은 [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md)을 참조 하십시오. DDX 및 DDV의 개요는 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md) 및 [대화 상자 항목](../../mfc/dialog-boxes.md)을 참조 하세요.

## <a name="cdataexchangem_bsaveandvalidate"></a><a name="m_bsaveandvalidate"></a> CDataExchange:: m_bSaveAndValidate

이 플래그는 DDX (대화 상자 데이터 교환) 작업의 방향을 나타냅니다.

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>설명

`CDataExchange`사용자가 컨트롤을 편집한 후 개체를 사용 하 여 대화 상자 컨트롤에서 대화 상자 클래스 데이터 멤버로 데이터를 이동 하는 경우 플래그는 0이 아닙니다. 대화 상자 클래스 데이터 멤버에서 대화 상자 컨트롤을 초기화 하는 데 개체가 사용 되는 경우 플래그는 0입니다.

DDV (대화 상자 데이터 유효성 검사) 중에도 플래그는 0이 아닙니다.

사용자 고유의 DDX 및 DDV 루틴을 작성 하는 방법에 대 한 자세한 내용은 [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md)을 참조 하십시오. DDX 및 DDV의 개요는 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md) 및 [대화 상자 항목](../../mfc/dialog-boxes.md)을 참조 하세요.

## <a name="cdataexchangem_pdlgwnd"></a><a name="m_pdlgwnd"></a> CDataExchange:: m_pDlgWnd

DDX (대화 상자 데이터 교환) 또는 유효성 검사 (DDV)가 수행 되는 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 포인터를 포함 합니다.

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>설명

이 개체는 일반적으로 [CDialog](../../mfc/reference/cdialog-class.md) 개체입니다. 사용자 지정 DDX 또는 DDV 루틴의 구현자는이 포인터를 사용 하 여 작동 하는 컨트롤이 포함 된 대화 상자 창에 대 한 액세스 권한을 얻을 수 있습니다.

사용자 고유의 DDX 및 DDV 루틴을 작성 하는 방법에 대 한 자세한 내용은 [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md)을 참조 하십시오. DDX 및 DDV의 개요는 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md) 및 [대화 상자 항목](../../mfc/dialog-boxes.md)을 참조 하세요.

## <a name="cdataexchangepreparectrl"></a><a name="preparectrl"></a> CDataExchange::P repareCtrl

프레임 워크는이 멤버 함수를 호출 하 여 DDX (대화 상자 데이터 교환) 및 유효성 검사 (DDV)에 대해 지정 된 컨트롤을 준비 합니다.

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>매개 변수

*nIDC*<br/>
DDX 또는 DDV에 대해 준비할 컨트롤의 ID입니다.

### <a name="return-value"></a>반환 값

DDX 또는 DDV에 대해 준비 되는 컨트롤의 HWND입니다.

### <a name="remarks"></a>설명

편집 컨트롤에 대해 대신 [Prepareeditctrl](#prepareeditctrl) 를 사용 합니다. 다른 모든 컨트롤에 대해이 멤버 함수를 사용 합니다.

준비는 클래스에 컨트롤의 HWND를 저장 하는 것으로 구성 됩니다 `CDataExchange` . 프레임 워크는이 핸들을 사용 하 여 DDX 또는 DDV 오류가 발생할 경우 이전에 포커스가 있는 컨트롤로 포커스를 복원 합니다.

사용자 지정 DDX 또는 DDV 루틴의 구현자는 `PrepareCtrl` ddx를 통해 데이터를 교환 하거나 DDV를 통해 데이터의 유효성을 검사 하는 모든 비 편집 컨트롤에 대해를 호출 해야 합니다.

사용자 고유의 DDX 및 DDV 루틴을 작성 하는 방법에 대 한 자세한 내용은 [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md)을 참조 하십시오. DDX 및 DDV의 개요는 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md) 및 [대화 상자 항목](../../mfc/dialog-boxes.md)을 참조 하세요.

## <a name="cdataexchangeprepareeditctrl"></a><a name="prepareeditctrl"></a> CDataExchange::P repareEditCtrl

프레임 워크는이 멤버 함수를 호출 하 여 DDX (대화 상자 데이터 교환) 및 유효성 검사 (DDV)에 대해 지정 된 편집 컨트롤을 준비 합니다.

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>매개 변수

*nIDC*<br/>
DDX 또는 DDV에 대해 준비할 편집 컨트롤의 ID입니다.

### <a name="return-value"></a>반환 값

DDX 또는 DDV에 대해 준비 중인 edit 컨트롤의 HWND입니다.

### <a name="remarks"></a>설명

모든 비 편집 컨트롤에 대해 대신 [PrepareCtrl](#preparectrl) 를 사용 합니다.

준비는 두 가지로 구성 됩니다. 먼저 `PrepareEditCtrl` 클래스에 컨트롤의 HWND를 저장 합니다 `CDataExchange` . 프레임 워크는이 핸들을 사용 하 여 DDX 또는 DDV 오류가 발생할 경우 이전에 포커스가 있는 컨트롤로 포커스를 복원 합니다. 둘째, `PrepareEditCtrl` 클래스에서 플래그를 설정 `CDataExchange` 하 여 데이터를 교환 하거나 유효성을 검사 하는 컨트롤이 편집 컨트롤 임을 표시 합니다.

사용자 지정 DDX 또는 DDV 루틴의 구현자는 `PrepareEditCtrl` ddx를 통해 데이터를 교환 하거나 DDV를 통해 데이터의 유효성을 검사 하는 모든 편집 컨트롤에 대해를 호출 해야 합니다.

사용자 고유의 DDX 및 DDV 루틴을 작성 하는 방법에 대 한 자세한 내용은 [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md)을 참조 하십시오. DDX 및 DDV의 개요는 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md) 및 [대화 상자 항목](../../mfc/dialog-boxes.md)을 참조 하세요.

## <a name="cdataexchangeprepareolectrl"></a><a name="prepareolectrl"></a> CDataExchange::P repareOleCtrl

프레임 워크는이 멤버 함수를 호출 하 여 DDX (대화 상자 데이터 교환) 및 유효성 검사 (DDV)에 대해 지정 된 OLE 컨트롤을 준비 합니다.

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>매개 변수

*nIDC*<br/>
DDX 또는 DDV에 대해 준비할 OLE 컨트롤의 ID입니다.

### <a name="return-value"></a>반환 값

OLE 컨트롤 사이트에 대 한 포인터입니다.

### <a name="remarks"></a>설명

다른 모든 비 OLE 컨트롤에 대해 edit controls 또는 [PrepareCtrl](#preparectrl) 에 대해 대신 [prepareeditctrl](#prepareeditctrl) 를 사용 합니다.

사용자 지정 DDX 또는 DDV 루틴의 구현자는 `PrepareOleCtrl` ddx를 통해 데이터를 교환 하거나 DDV를 통해 데이터의 유효성을 검사 하는 모든 OLE 컨트롤에 대해를 호출 해야 합니다.

사용자 고유의 DDX 및 DDV 루틴을 작성 하는 방법에 대 한 자세한 내용은 [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md)을 참조 하십시오. DDX 및 DDV의 개요는 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md) 및 [대화 상자 항목](../../mfc/dialog-boxes.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)
