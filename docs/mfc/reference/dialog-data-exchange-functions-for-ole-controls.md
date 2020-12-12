---
description: '자세한 정보: OLE 컨트롤에 대 한 대화 상자 데이터 교환 함수'
title: OLE 컨트롤에 대한 대화 상자 데이터 교환 함수
ms.date: 11/04/2016
f1_keywords:
- AFXDISP/DDX_OCBool
- AFXDISP/DDX_OCBoolRO
- AFXDISP/DDX_OCColor
- AFXDISP/DDX_OCColorRO
- AFXDISP/DDX_OCFloat
- AFXDISP/DDX_OCFloatRO
- AFXDISP/DDX_OCInt
- AFXDISP/DDX_OCIntRO
- AFXDISP/DDX_OCShort
- AFXDISP/DDX_OCShortRO
- AFXDISP/DDX_OCText
- AFXDISP/DDX_OCTextRO
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
ms.openlocfilehash: ed2a3c36655ce5fccf482c0a7dedad0a4c67baa5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219956"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>OLE 컨트롤에 대한 대화 상자 데이터 교환 함수

이 항목에서는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 속성과 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버 간에 데이터를 교환 하는 데 사용 되는 DDX_OC 함수를 나열 합니다.

### <a name="ddx_oc-functions"></a>DDX_OC 함수

|Name|설명|
|-|-|
|[DDX_OCBool](#ddx_ocbool)|OLE 컨트롤의 속성과 **bool** 데이터 멤버 간의 **bool** 데이터 전송을 관리 합니다.|
|[DDX_OCBoolRO](#ddx_ocboolro)|OLE 컨트롤의 읽기 전용 속성과 **bool** 데이터 멤버 간의 **bool** 데이터 전송을 관리 합니다.|
|[DDX_OCColor](#ddx_occolor)|OLE 컨트롤의 속성과 **OLE_COLOR** 데이터 멤버 간의 **OLE_COLOR** 데이터 전송을 관리 합니다.|
|[DDX_OCColorRO](#ddx_occolorro)|OLE 컨트롤의 읽기 전용 속성과 **OLE_COLOR** 데이터 멤버 간의 **OLE_COLOR** 데이터 전송을 관리 합니다.|
|[DDX_OCFloat](#ddx_ocfloat)|**`float`** **`double`** OLE 컨트롤과 **`float`** (또는) 데이터 멤버의 속성 간에 (또는) 데이터 전송을 관리 합니다 **`double`** .|
|[DDX_OCFloatRO](#ddx_ocfloatro)|**`float`** **`double`** OLE 컨트롤의 읽기 전용 속성과 **`float`** (또는) 데이터 멤버 간의 (또는) 데이터 전송을 관리 합니다 **`double`** .|
|[DDX_OCInt](#ddx_ocint)|**`int`** **`long`** OLE 컨트롤과 **`int`** (또는) 데이터 멤버의 속성 간에 (또는) 데이터 전송을 관리 합니다 **`long`** .|
|[DDX_OCIntRO](#ddx_ocintro)|**`int`** **`long`** OLE 컨트롤의 읽기 전용 속성과 **`int`** (또는) 데이터 멤버 간의 (또는) 데이터 전송을 관리 합니다 **`long`** .|
|[DDX_OCShort](#ddx_ocshort)|**`short`** OLE 컨트롤과 데이터 멤버의 속성 간 데이터 전송을 관리 합니다 **`short`** .|
|[DDX_OCShortRO](#ddx_ocshortro)|**`short`** OLE 컨트롤의 읽기 전용 속성과 데이터 멤버 간의 데이터 전송을 관리 합니다 **`short`** .|
|[DDX_OCText](#ddx_octext)|OLE 컨트롤과 **cstring** 데이터 멤버의 속성 간에 **cstring** 데이터의 전송을 관리 합니다.|
|[DDX_OCTextRO](#ddx_octextro)|OLE 컨트롤의 읽기 전용 속성과 **cstring** 데이터 멤버 간의 **cstring** 데이터 전송을 관리 합니다.|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a> DDX_OCBool

함수는 대화 `DDX_OCBool` 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 속성과 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 **bool** 데이터 멤버 사이에서 **bool** 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.

*dispid*<br/>
컨트롤의 속성에 대한 디스패치 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더:** afxdisp.h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a> DDX_OCBoolRO

함수는 대화 `DDX_OCBoolRO` 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤에 대 한 읽기 전용 속성과 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 **bool** 데이터 멤버 사이에서 **bool** 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.

*dispid*<br/>
컨트롤의 속성에 대한 디스패치 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a> DDX_OCColor

함수는 대화 `DDX_OCColor` 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 속성과 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE_COLOR 데이터 멤버 간의 OLE_COLOR 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.

*dispid*<br/>
컨트롤의 속성에 대한 디스패치 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a> DDX_OCColorRO

함수는 대화 `DDX_OCColorRO` 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤에 대 한 읽기 전용 속성과 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE_COLOR 데이터 멤버 간에 OLE_COLOR 데이터 전송을 관리 합니다.

```cpp
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.

*dispid*<br/>
컨트롤의 속성에 대한 디스패치 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a> DDX_OCFloat

함수는 대화 `DDX_OCFloat` **`float`** 상자, **`double`** 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 속성과 **`float`** **`double`** 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 (또는) 데이터 멤버 사이에 있는 (또는) 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.

*dispid*<br/>
컨트롤의 속성에 대한 디스패치 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a> DDX_OCFloatRO

함수는 대화 `DDX_OCFloatRO` **`float`** 상자, **`double`** 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤에 대 한 읽기 전용 속성과 **`float`** **`double`** 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 (또는) 데이터 멤버 사이에 있는 (또는) 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.

*dispid*<br/>
컨트롤의 속성에 대한 디스패치 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a> DDX_OCInt

함수는 대화 `DDX_OCInt` **`int`** 상자, **`long`** 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 속성과 **`int`** **`long`** 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 (또는) 데이터 멤버 사이에 있는 (또는) 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.

*dispid*<br/>
컨트롤의 속성에 대한 디스패치 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a> DDX_OCIntRO

함수는 대화 `DDX_OCIntRO` **`int`** 상자, **`long`** 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤에 대 한 읽기 전용 속성과 **`int`** **`long`** 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 (또는) 데이터 멤버 사이에 있는 (또는) 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.

*dispid*<br/>
컨트롤의 속성에 대한 디스패치 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a> DDX_OCShort

함수는 대화 `DDX_OCShort` 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 속성과 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 short 데이터 멤버 간에 짧은 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.

*dispid*<br/>
컨트롤의 속성에 대한 디스패치 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a> DDX_OCShortRO

함수는 대화 `DDX_OCShortRO` 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤에 대 한 읽기 전용 속성과 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 short 데이터 멤버 간에 짧은 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.

*dispid*<br/>
컨트롤의 속성에 대한 디스패치 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="ddx_octext"></a><a name="ddx_octext"></a> DDX_OCText

**DDX_OCText** 함수는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 속성과 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 **cstring** 데이터 멤버 간에 **cstring** 데이터의 전송을 관리 합니다.

```cpp
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
**CDataExchange** 개체에 대 한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.

*dispid*<br/>
컨트롤의 속성에 대한 디스패치 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="ddx_octextro"></a><a name="ddx_octextro"></a> DDX_OCTextRO

`DDX_OCTextRO` 함수는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체 내 OLE 컨트롤의 읽기 전용 속성과 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 `CString` 데이터 멤버 간 `CString` 데이터 전송을 관리합니다.

```cpp
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*nIDC*<br/>
대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.

*dispid*<br/>
컨트롤의 속성에 대한 디스패치 ID입니다.

*value*<br/>
데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.

### <a name="remarks"></a>설명

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
