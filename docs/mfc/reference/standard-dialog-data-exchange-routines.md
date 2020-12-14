---
description: '자세한 정보: 표준 대화 상자 데이터 교환 루틴'
title: 표준 대화 상자 데이터 교환 루틴
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: f1d5cb0726168b90e0ba2a7891ce0ffa55b73f10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218864"
---
# <a name="standard-dialog-data-exchange-routines"></a>표준 대화 상자 데이터 교환 루틴

이 항목에서는 일반적인 MFC 대화 상자 컨트롤에 사용 되는 표준 DDX (대화 상자 데이터 교환) 루틴을 나열 합니다.

> [!NOTE]
> 표준 대화 상자 데이터 교환 루틴은 헤더 파일 afxdd_에 정의 되어 있습니다. 그러나 응용 프로그램은 afxwin.h를 포함 해야 합니다.

### <a name="ddx-functions"></a>DDX 함수

|Name|설명|
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|현재 선택 된 콤보 상자 컨트롤의 인덱스를 초기화 하거나 검색 합니다.|
|[DDX_CBString](#ddx_cbstring)|콤보 상자 컨트롤의 편집 필드 현재 내용을 초기화 하거나 검색 합니다.|
|[DDX_CBStringExact](#ddx_cbstringexact)|콤보 상자 컨트롤의 편집 필드 현재 내용을 초기화 하거나 검색 합니다.|
|[DDX_Check](#ddx_check)|확인란 컨트롤의 현재 상태를 초기화 하거나 검색 합니다.|
|[DDX_Control](#ddx_control)|대화 상자 내에서 지정 된 컨트롤을 서브 클래스 합니다.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|날짜 및 시간 선택 컨트롤의 날짜 및/또는 시간 데이터를 초기화 하거나 검색 합니다.|
|[DDX_IPAddress](#ddx_ipaddress)|IP 주소 컨트롤의 현재 값을 초기화 하거나 검색 합니다.|
|[DDX_LBIndex](#ddx_lbindex)|목록 상자 컨트롤의 현재 선택 영역에 대 한 인덱스를 초기화 하거나 검색 합니다.|
|[DDX_LBString](#ddx_lbstring)|목록 상자 컨트롤에서 현재 선택 영역을 초기화 하거나 검색 합니다.|
|[DDX_LBStringExact](#ddx_lbstringexact)|목록 상자 컨트롤에서 현재 선택 영역을 초기화 하거나 검색 합니다.|
|[DDX_ManagedControl](#ddx_managedcontrol)|컨트롤의 리소스 ID와 일치 하는 .NET 컨트롤을 만듭니다.|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Month calendar 컨트롤의 현재 값을 초기화 하거나 검색 합니다.|
|[DDX_Radio](#ddx_radio)|라디오 컨트롤 그룹 내에서 현재 확인 된 라디오 컨트롤의 인덱스 (0부터 사용)를 초기화 하거나 검색 합니다.|
|[DDX_Scroll](#ddx_scroll)|Scroll 컨트롤의 thumb의 현재 위치를 초기화 하거나 검색 합니다.|
|[DDX_Slider](#ddx_slider)|슬라이더 컨트롤 엄지 단추의 현재 위치를 초기화 하거나 검색 합니다.|
|[DDX_Text](#ddx_text)|편집 컨트롤의 현재 값을 초기화 하거나 검색 합니다.|

## <a name="ddx_cbindex"></a><a name="ddx_cbindex"></a> DDX_CBIndex

함수는 대화 `DDX_CBIndex` **`int`** 상자, 폼 뷰 또는 컨트롤 뷰 개체의 콤보 상자 컨트롤과 **`int`** 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버 간 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
컨트롤 속성과 연결 된 콤보 상자 컨트롤의 리소스 ID입니다.

*index*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

### <a name="remarks"></a>설명

`DDX_CBIndex`가 호출 되 면 *인덱스* 는 현재 콤보 상자 선택 항목의 인덱스로 설정 됩니다. 항목을 선택 하지 않으면 *인덱스* 는 0으로 설정 됩니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_cbstring"></a><a name="ddx_cbstring"></a> DDX_CBString

함수는 대화 상자, `DDX_CBString` `CString` 폼 뷰 또는 컨트롤 뷰 개체의 콤보 상자 컨트롤의 편집 컨트롤과 `CString` 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버 간 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
컨트롤 속성과 연결 된 콤보 상자 컨트롤의 리소스 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

### <a name="remarks"></a>설명

`DDX_CBString`가 호출 되 면 *값* 이 현재 콤보 상자 선택 항목으로 설정 됩니다. 항목을 선택 하지 않으면 *값* 이 길이가 0 인 문자열로 설정 됩니다.

> [!NOTE]
> 콤보 상자가 드롭다운 목록 상자 이면 교환 되는 값은 255 자로 제한 됩니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_cbstringexact"></a><a name="ddx_cbstringexact"></a> DDX_CBStringExact

함수는 대화 상자, `DDX_CBStringExact` `CString` 폼 뷰 또는 컨트롤 뷰 개체의 콤보 상자 컨트롤의 편집 컨트롤과 `CString` 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버 간 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
컨트롤 속성과 연결 된 콤보 상자 컨트롤의 리소스 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

### <a name="remarks"></a>설명

`DDX_CBStringExact`가 호출 되 면 *값* 이 현재 콤보 상자 선택 항목으로 설정 됩니다. 항목을 선택 하지 않으면 *값* 이 길이가 0 인 문자열로 설정 됩니다.

> [!NOTE]
> 콤보 상자가 드롭다운 목록 상자 이면 교환 되는 값은 255 자로 제한 됩니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_check"></a><a name="ddx_check"></a> DDX_Check

함수는 대화 `DDX_Check` **`int`** 상자, 폼 뷰 또는 컨트롤 뷰 개체의 확인란 컨트롤과 **`int`** 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버 간 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
컨트롤 속성과 연결 된 확인란 컨트롤의 리소스 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

### <a name="remarks"></a>설명

`DDX_Check`가 호출 되 면 *값* 이 확인란 컨트롤의 현재 상태로 설정 됩니다. 가능한 상태 값 목록은 Windows SDK에서 [BM_GETCHECK](/windows/win32/Controls/bm-getcheck) 을 참조 하세요.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_control"></a><a name="ddx_control"></a> DDX_Control

`DDX_Control`함수는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 *nidc* 에 의해 지정 된 컨트롤을 하위 클래스로 지정 합니다.

```cpp
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*nIDC*<br/>
서브클래싱된 컨트롤의 리소스 ID입니다.

*rControl*<br/>
지정 된 컨트롤과 관련 된 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

### <a name="remarks"></a>설명

*PDX* 개체는 함수가 호출 될 때 프레임 워크에서 제공 됩니다 `DoDataExchange` . 따라서는 `DDX_Control` 재정의 내에서 호출 해야 합니다 `DoDataExchange` .

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_datetimectrl"></a><a name="ddx_datetimectrl"></a> DDX_DateTimeCtrl

`DDX_DateTimeCtrl`함수는 대화 상자 또는 폼 뷰 개체의 날짜 및 시간 선택 컨트롤 ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md))과 대화 상자 또는 폼 뷰 개체의 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 또는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 데이터 멤버 간에 날짜 및/또는 시간 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다. 이 개체를 삭제할 필요는 없습니다.

*nIDC*<br/>
멤버 변수와 연결 된 날짜 및 시간 선택 컨트롤의 리소스 ID입니다.

*value*<br/>
처음 두 버전에서는 데이터를 교환 하는 `CTime` 또는 `COleDateTime` 멤버 변수, 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체에 대 한 참조입니다. 세 번째 버전에서 `CString` 데이터 멤버 컨트롤 뷰 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

`DDX_DateTimeCtrl`가 호출 되 면 *값* 이 날짜 및 시간 선택 컨트롤의 현재 상태로 설정 되거나 exchange의 방향에 따라 컨트롤이 *값* 으로 설정 됩니다.

위의 세 번째 버전에서는 `DDX_DateTimeCtrl` `CString` 컨트롤 뷰 개체의 날짜/시간 컨트롤과 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 데이터 멤버 간의 데이터 전송을 관리 합니다. 문자열은 날짜 및 시간 형식을 지정 하기 위해 현재 로캘의 규칙을 사용 하 여 형식이 지정 됩니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_managedcontrol"></a><a name="ddx_managedcontrol"></a> DDX_ManagedControl

컨트롤의 리소스 ID와 일치 하는 .NET 컨트롤을 만듭니다.

### <a name="syntax"></a>구문

```cpp
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange 클래스](cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
컨트롤 속성과 연결 된 컨트롤의 리소스 ID입니다.

*control*<br/>
[CWinFormsControl 클래스](cwinformscontrol-class.md) 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

`DDX_ManagedControl`[CWinFormsControl:: CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) 를 호출 하 여 리소스 컨트롤 ID와 일치 하는 컨트롤을 만듭니다. `DDX_ManagedControl`을 사용 하 여 [CDialog:: OnInitDialog](cdialog-class.md#oninitdialog)의 리소스 id에서 컨트롤을 만듭니다. 데이터 교환의 경우 Windows Forms 컨트롤에서 DDX/DDV 함수를 사용할 필요가 없습니다.

자세한 내용은 [방법: Windows Forms를 사용 하 여 DDX/DDV 데이터 바인딩 수행](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxwinforms

## <a name="ddx_ipaddress"></a><a name="ddx_ipaddress"></a> DDX_IPAddress

`DDX_IPAddress`함수는 IP 주소 컨트롤과 컨트롤 뷰 개체의 데이터 멤버 간 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
컨트롤 속성에 연결 된 IP 주소 컨트롤의 리소스 ID입니다.

*value*<br/>
IP 주소 컨트롤의 네 필드 값을 포함 하는 DWORD에 대 한 참조입니다. 필드는 다음과 같이 채우거 나 읽습니다.

|필드|필드 값을 포함 하는 비트|
|-----------|-------------------------------------|
|3|0-7|
|2|8-15|
|1|16-23|
|0|24 ~ 31|

Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) 를 사용 하 여 값을 읽거나 [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress) 를 사용 하 여 값을 채웁니다. 이러한 메시지는 Windows SDK에 설명 되어 있습니다.

### <a name="remarks"></a>설명

`DDX_IPAddress`가 호출 되 면 IP 주소 컨트롤에서 *값* 을 읽거나 exchange의 방향에 따라 *값* 을 컨트롤에 씁니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_lbindex"></a><a name="ddx_lbindex"></a> DDX_LBIndex

함수는 대화 `DDX_LBIndex` **`int`** 상자, 폼 뷰 또는 컨트롤 뷰 개체의 목록 상자 컨트롤과 **`int`** 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버 간 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
컨트롤 속성과 연결 된 목록 상자 컨트롤의 리소스 ID입니다.

*index*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

### <a name="remarks"></a>설명

`DDX_LBIndex`가 호출 되 면 *인덱스* 는 현재 목록 상자 선택 항목의 인덱스로 설정 됩니다. 항목을 선택 하지 않으면 *인덱스* 는-1로 설정 됩니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_lbstring"></a><a name="ddx_lbstring"></a> DDX_LBString

함수는 대화 `DDX_LBString` `CString` 상자, 폼 뷰 또는 컨트롤 뷰 개체의 목록 상자 컨트롤과 `CString` 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버 간 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
컨트롤 속성과 연결 된 목록 상자 컨트롤의 리소스 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

### <a name="remarks"></a>설명

`DDX_LBString`목록 상자 컨트롤에 데이터를 전송 하기 위해가 호출 되 면 컨트롤에서 시작 *값* 과 일치 하는 첫 번째 항목이 선택 됩니다. (접두사가 아니라 전체 항목을 일치 시키려면 [DDX_LBStringExact](#ddx_lbstringexact)를 사용 합니다.) 일치 하는 항목이 없으면 선택 된 항목이 없습니다. 일치는 대/소문자를 구분 하지 않습니다.

`DDX_LBString`목록 상자 컨트롤에서 데이터를 전송 하기 위해가 호출 되 면 *값* 이 현재 목록 상자 선택 항목으로 설정 됩니다. 항목을 선택 하지 않으면 *값* 이 길이가 0 인 문자열로 설정 됩니다.

> [!NOTE]
> 목록 상자가 드롭다운 목록 상자 이면 교환 되는 값은 255 자로 제한 됩니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_lbstringexact"></a><a name="ddx_lbstringexact"></a> DDX_LBStringExact

함수는 대화 상자, `DDX_CBStringExact` `CString` 폼 뷰 또는 컨트롤 뷰 개체와 `CString` 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버에 있는 목록 상자 컨트롤의 편집 컨트롤 간 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
컨트롤 속성과 연결 된 목록 상자 컨트롤의 리소스 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

### <a name="remarks"></a>설명

`DDX_LBStringExact`목록 상자 컨트롤에 데이터를 전송 하기 위해가 호출 되 면 컨트롤에서 *값* 과 일치 하는 첫 번째 항목이 선택 됩니다. (전체 항목이 아닌 접두사만 일치 시키려면 [DDX_LBString](#ddx_lbstring)를 사용 합니다.) 일치 하는 항목이 없으면 선택 된 항목이 없습니다. 일치는 대/소문자를 구분 하지 않습니다.

`DDX_CBStringExact`목록 상자 컨트롤에서 데이터를 전송 하기 위해가 호출 되 면 *값* 이 현재 목록 상자 선택 항목으로 설정 됩니다. 항목을 선택 하지 않으면 *값* 이 길이가 0 인 문자열로 설정 됩니다.

> [!NOTE]
> 목록 상자가 드롭다운 목록 상자 이면 교환 되는 값은 255 자로 제한 됩니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_monthcalctrl"></a><a name="ddx_monthcalctrl"></a> DDX_MonthCalCtrl

`DDX_MonthCalCtrl`함수는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 monthcalendar 컨트롤 ( [Cmonthcalctrl](../../mfc/reference/cmonthcalctrl-class.md))과 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 또는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 데이터 멤버 간에 날짜 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다. 이 개체를 삭제할 필요는 없습니다.

*nIDC*<br/>
멤버 변수와 연결 된 month calendar 컨트롤의 리소스 ID입니다.

*value*<br/>
`CTime` `COleDateTime` 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 또는 멤버 변수에 대 한 참조입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> 컨트롤은 날짜 값만 관리 합니다. 시간 개체의 시간 필드는 컨트롤 창의 만든 시간을 반영 하거나를 호출 하 여 컨트롤에 설정 된 시간을 반영 하 여 설정 됩니다 `CMonthCalCtrl::SetCurSel` .

`DDX_MonthCalCtrl`가 호출 되 면 *값* 이 month calendar 컨트롤의 현재 상태로 설정 됩니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_radio"></a><a name="ddx_radio"></a> DDX_Radio

함수는 대화 `DDX_Radio` **`int`** 상자, 폼 뷰 또는 컨트롤 뷰 개체의 라디오 컨트롤 그룹과 **`int`** 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버 간 데이터 전송을 관리 합니다. 데이터 멤버의 값은 **`int`** 선택 된 그룹 내의 라디오 단추에 따라 결정 됩니다.

```cpp
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
그룹에 있는 첫 번째 라디오 컨트롤의 리소스 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

### <a name="remarks"></a>설명

`DDX_Radio`가 호출 되 면 *값* 이 라디오 컨트롤 그룹의 현재 상태로 설정 됩니다. 이 값은 현재 선택 된 라디오 컨트롤의 0부터 기반 하는 인덱스로 설정 되며, 선택 된 라디오 컨트롤이 없으면-1입니다.

예를 들어 그룹의 첫 번째 라디오 단추를 선택 하는 경우 (WS_GROUP 스타일이 있는 단추) 멤버 값은 **`int`** 0이 됩니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_scroll"></a><a name="ddx_scroll"></a> DDX_Scroll

`DDX_Scroll`함수는 **`int`** 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 스크롤 막대 컨트롤과 **`int`** 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버 간 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
컨트롤 속성과 연결 된 스크롤 막대 컨트롤의 리소스 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

`DDX_Scroll`가 호출 되 면 *값* 이 컨트롤의 현재 위치로 설정 됩니다. 컨트롤의 현재 위치와 연결 된 값에 대 한 자세한 내용은 Windows SDK의 [GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) 를 참조 하세요.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_slider"></a><a name="ddx_slider"></a> DDX_Slider

`DDX_Slider`함수는 **`int`** 대화 상자 또는 폼 보기의 슬라이더 컨트롤과 **`int`** 대화 상자 또는 폼 뷰 개체의 데이터 멤버 간 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
슬라이더 컨트롤의 리소스 ID입니다.

*value*<br/>
교환할 값에 대 한 참조입니다. 이 매개 변수는 슬라이더 컨트롤의 현재 위치를 포함 하거나 설정 합니다.

### <a name="remarks"></a>설명

`DDX_Slider`가 호출 되 면 *값* 이 컨트롤의 현재 위치에 대 한 값으로 설정 되거나, exchange의 방향에 따라 값이 위치를 수신 합니다.

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. 슬라이더 컨트롤에 대 한 자세한 내용은 [CSliderCtrl 사용](../../mfc/using-csliderctrl.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddx_text"></a><a name="ddx_text"></a> DDX_Text

함수는 대화 상자, `DDX_Text` **`int`**  **`long`** `CString` **`float`** **`double`** 폼 뷰 또는 컨트롤 뷰의 편집 컨트롤과 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 데이터 멤버 사이에서, UINT,, DWORD,, 또는 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    short& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    int& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    UINT& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    long& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    CString& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    float& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    double& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 편집 컨트롤 ID입니다.

*value*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버에 대 한 참조입니다. *값* 의 데이터 형식은 사용 하는 오버 로드 된 버전에 따라 다릅니다 `DDX_Text` .

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="see-also"></a>참고 항목

[표준 대화 상자 데이터 유효성 검사 루틴](standard-dialog-data-validation-routines.md)<br/>
[매크로 및 전역](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
