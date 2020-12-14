---
description: '자세한 정보: 표준 대화 상자 데이터 유효성 검사 루틴'
title: 표준 대화 상자 데이터 유효성 검사 루틴
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: d2b39381610c51f661e98256c39b580df256ebaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218851"
---
# <a name="standard-dialog-data-validation-routines"></a>표준 대화 상자 데이터 유효성 검사 루틴

이 항목에서는 일반적인 MFC 대화 상자 컨트롤에 사용 되는 표준 DDV (대화 상자 데이터 유효성 검사) 루틴을 나열 합니다.

> [!NOTE]
> 표준 대화 상자 데이터 교환 루틴은 헤더 파일 afxdd_에 정의 되어 있습니다. 그러나 응용 프로그램은 afxwin.h를 포함 해야 합니다.

### <a name="ddv-functions"></a>DDV 함수

|Name|설명|
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|지정 된 컨트롤 값의 문자 수가 지정 된 최대값을 초과 하지 않는지 확인 합니다.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|지정 된 컨트롤 값이 지정 된 **바이트** 범위를 초과 하지 않는지 확인 합니다.|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|지정 된 컨트롤 값이 지정 된 시간 범위를 초과 하지 않는지 확인 합니다.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|지정 된 컨트롤 값이 지정 된 범위를 초과 하지 않는지 확인 **`double`** 합니다.|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|지정 된 컨트롤 값이 지정 된 **DWORD** 범위를 초과 하지 않는지 확인 합니다.|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|지정 된 컨트롤 값이 지정 된 범위를 초과 하지 않는지 확인 **`float`** 합니다.|
|[DDV_MinMaxInt](#ddv_minmaxint)|지정 된 컨트롤 값이 지정 된 범위를 초과 하지 않는지 확인 **`int`** 합니다.|
|[DDV_MinMaxLong](#ddv_minmaxlong)|지정 된 컨트롤 값이 지정 된 범위를 초과 하지 않는지 확인 **`long`** 합니다.|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|지정 된 컨트롤 값이 지정 된 **시간** 범위를 초과 하지 않는지 확인 합니다.|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|지정 된 컨트롤 값이 지정 된 날짜 범위를 초과 하지 않는지 확인 합니다.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|지정 된 컨트롤 값이 지정 된 범위를 초과 하지 않는지 확인 **`short`** 합니다.|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|지정 된 슬라이더 컨트롤 값이 지정 된 범위 내에 속하는지 확인 합니다.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|지정 된 컨트롤 값이 지정 된 **UINT** 범위를 초과 하지 않는지 확인 합니다.|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|지정 된 컨트롤 값이 지정 된 두 값 사이에 속하는지 확인 합니다.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|지정 된 컨트롤 값이 지정 된 **ULONGLONG** 범위를 초과 하지 않는지 확인 합니다.|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a> DDV_MaxChars

`DDV_MaxChars`를 호출 하 여 *값* 과 연결 된 컨트롤의 문자 크기가 *nchars* 를 초과 하지 않는지 확인 합니다.

```cpp
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
데이터의 유효성을 검사 하는 데 사용 되는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*nChars*<br/>
허용 되는 최대 문자 수입니다.

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a> DDV_MinMaxByte

`DDV_MinMaxByte`을 호출 하 여 *값* 과 연결 된 컨트롤의 값이 *minval* 과 *maxval* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
데이터의 유효성을 검사 하는 데 사용 되는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*minVal*<br/>
허용 되는 최소 값 (바이트 형식)입니다.

*maxVal*<br/>
허용 되는 최대 값 (바이트 형식)입니다.

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a> DDV_MinMaxDateTime

`DDV_MinMaxDateTime`을 호출 하 여 *refvalue* 와 연결 된 날짜 및 시간 선택 컨트롤 ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md))의 시간/날짜 값이 *refMinRange* 와 *refMaxRange* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다. 이 개체를 삭제할 필요는 없습니다.

*refValue*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수와 연결 된 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 또는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체에 대 한 참조입니다. 이 개체는 유효성을 검사할 데이터를 포함 합니다.

*refMinRange*<br/>
허용 되는 최소 날짜/시간 값입니다.

*refMaxRange*<br/>
허용 되는 최대 날짜/시간 값입니다.

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a> DDV_MinMaxDouble

`DDV_MinMaxDouble`을 호출 하 여 *값* 과 연결 된 컨트롤의 값이 *minval* 과 *maxval* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
데이터의 유효성을 검사 하는 데 사용 되는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*minVal*<br/>
허용 되는 최소 값 유형입니다 **`double`** .

*maxVal*<br/>
허용 되는 최대 값 유형입니다 **`double`** .

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a> DDV_MinMaxDWord

`DDV_MinMaxDWord`을 호출 하 여 *값* 과 연결 된 컨트롤의 값이 *minval* 과 *maxval* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
데이터의 유효성을 검사 하는 데 사용 되는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*minVal*<br/>
허용 되는 최소 값 (DWORD 형식)입니다.

*maxVal*<br/>
허용 되는 최대 값 (DWORD 형식)입니다.

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a> DDV_MinMaxFloat

`DDV_MinMaxFloat`을 호출 하 여 *값* 과 연결 된 컨트롤의 값이 *minval* 과 *maxval* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
데이터의 유효성을 검사 하는 데 사용 되는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*minVal*<br/>
허용 되는 최소 값 유형입니다 **`float`** .

*maxVal*<br/>
허용 되는 최대 값 유형입니다 **`float`** .

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a> DDV_MinMaxInt

`DDV_MinMaxInt`을 호출 하 여 *값* 과 연결 된 컨트롤의 값이 *minval* 과 *maxval* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
데이터의 유효성을 검사 하는 데 사용 되는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*minVal*<br/>
허용 되는 최소 값 유형입니다 **`int`** .

*maxVal*<br/>
허용 되는 최대 값 유형입니다 **`int`** .

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a> DDV_MinMaxLong

`DDV_MinMaxLong`을 호출 하 여 *값* 과 연결 된 컨트롤의 값이 *minval* 과 *maxval* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
데이터의 유효성을 검사 하는 데 사용 되는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*minVal*<br/>
허용 되는 최소 값 유형입니다 **`long`** .

*maxVal*<br/>
허용 되는 최대 값 유형입니다 **`long`** .

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a> DDV_MinMaxLongLong

`DDV_MinMaxLongLong`을 호출 하 여 *값* 과 연결 된 컨트롤의 값이 *minval* 과 *maxval* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
데이터의 유효성을 검사 하는 데 사용 되는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*minVal*<br/>
허용 되는 최소 값 (형식)이 허용 됩니다.

*maxVal*<br/>
허용 되는 최대값 형식의 최대값입니다.

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a> DDV_MinMaxMonth

`DDV_MinMaxMonth`을 호출 하 여 *refvalue* 와 연결 된 month Calendar 컨트롤 ( [cmonthcalctrl](../../mfc/reference/cmonthcalctrl-class.md))의 시간/날짜 값이 *refMinRange* 과 *refMaxRange* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*refValue*<br/>
`CTime` `COleDateTime` 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수와 연결 된 형식의 개체에 대 한 참조입니다. 이 개체는 유효성을 검사할 데이터를 포함 합니다. MFC는가 호출 될 때이 참조 `DDV_MinMaxMonth` 를 전달 합니다.

*refMinRange*<br/>
허용 되는 최소 날짜/시간 값입니다.

*refMaxRange*<br/>
허용 되는 최대 날짜/시간 값입니다.

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a> DDV_MinMaxShort

`DDV_MinMaxShort`을 호출 하 여 *값* 과 연결 된 컨트롤의 값이 *minval* 과 *maxval* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
데이터의 유효성을 검사 하는 데 사용 되는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*minVal*<br/>
허용 되는 최소 값 유형입니다 **`short`** .

*maxVal*<br/>
허용 되는 최대 값 유형입니다 **`short`** .

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a> DDV_MinMaxSlider

`DDV_MinMaxSlider`을 호출 하 여 *값* 과 연결 된 컨트롤의 값이 *minval* 과 *maxval* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
유효성을 검사할 값에 대 한 참조입니다. 이 매개 변수는 슬라이더 컨트롤의 현재 엄지 단추 위치를 포함 하거나 설정 합니다.

*minVal*<br/>
허용 되는 최소값입니다.

*maxVal*<br/>
허용 되는 최대값입니다.

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요. 슬라이더 컨트롤에 대 한 자세한 내용은 [CSliderCtrl 사용](../../mfc/using-csliderctrl.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a> DDV_MinMaxUInt

`DDV_MinMaxUInt`을 호출 하 여 *값* 과 연결 된 컨트롤의 값이 *minval* 과 *maxval* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
데이터의 유효성을 검사 하는 데 사용 되는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*minVal*<br/>
허용 되는 최소값 (UINT 형식)입니다.

*maxVal*<br/>
허용 되는 최대 값 (UINT 형식)입니다.

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a> DDV_MinMaxULongLong

`DDV_MinMaxULongLong`을 호출 하 여 *값* 과 연결 된 컨트롤의 값이 *minval* 과 *maxval* 사이에 있는지 확인 합니다.

```cpp
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
데이터의 유효성을 검사 하는 데 사용 되는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*minVal*<br/>
허용 되는 최소 값 (ULONGLONG 형식)입니다.

*maxVal*<br/>
허용 되는 최대 값 (ULONGLONG 형식)입니다.

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdd_ .h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

`DDV_MinMaxUnsigned`을 호출 하 여 *값* 과 연결 된 컨트롤의 값이 *minval* 과 *maxval* 사이에 있는지 확인 합니다.

### <a name="syntax"></a>구문

```cpp
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*value*<br/>
데이터의 유효성을 검사 하는 데 사용 되는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대 한 참조입니다.

*minVal*<br/>
허용 되는 최소 값 유형입니다 **`unsigned`** .

*maxVal*<br/>
허용 되는 최대 값 유형입니다 **`unsigned`** .

### <a name="remarks"></a>설명

DDV에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../dialog-data-exchange-and-validation.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdd_. h

## <a name="see-also"></a>참고 항목

[표준 대화 상자 데이터 교환 루틴](standard-dialog-data-exchange-routines.md)<br/>
[매크로 및 전역](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
