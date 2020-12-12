---
description: '자세한 정보: OLE 컨트롤의 지 속성'
title: OLE 컨트롤의 지속성
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 8c0ee5b81ffd21953c3ed9bcbc21a9ae30979b49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218981"
---
# <a name="persistence-of-ole-controls"></a>OLE 컨트롤의 지속성

OLE 컨트롤의 한 가지 기능은 OLE 컨트롤에서 파일 또는 스트림으로 속성 값을 읽거나 쓸 수 있도록 하는 속성 지 속성 (또는 serialization)입니다. 응용 프로그램에서 컨트롤을 삭제 한 후에도 컨테이너 응용 프로그램은 serialization을 사용 하 여 컨트롤의 속성 값을 저장할 수 있습니다. 그런 다음 나중에 컨트롤의 새 인스턴스를 만들 때 파일 또는 스트림에서 OLE 컨트롤의 속성 값을 읽을 수 있습니다.

### <a name="persistence-of-ole-controls"></a>OLE 컨트롤의 지속성

|Name|설명|
|-|-|
|[PX_Blob](#px_blob)|BLOB (binary large object) 데이터를 저장 하는 컨트롤 속성을 교환 합니다.|
|[PX_Bool](#px_bool)|**BOOL** 형식의 컨트롤 속성을 교환 합니다.|
|[PX_Color](#px_color)|컨트롤의 색 속성을 교환 합니다.|
|[PX_Currency](#px_currency)|**CY** 형식의 컨트롤 속성을 교환 합니다.|
|[PX_DataPath](#px_datapath)|형식의 컨트롤 속성을 교환 `CDataPathProperty` 합니다.|
|[PX_Double](#px_double)|형식의 컨트롤 속성을 교환 **`double`** 합니다.|
|[PX_Font](#px_font)|컨트롤의 글꼴 속성을 교환 합니다.|
|[PX_Float](#px_float)|형식의 컨트롤 속성을 교환 **`float`** 합니다.|
|[PX_IUnknown](#px_iunknown)|정의 되지 않은 형식의 컨트롤 속성을 교환 합니다.|
|[PX_Long](#px_long)|형식의 컨트롤 속성을 교환 **`long`** 합니다.|
|[PX_Picture](#px_picture)|컨트롤의 그림 속성을 교환 합니다.|
|[PX_Short](#px_short)|형식의 컨트롤 속성을 교환 **`short`** 합니다.|
|[PX_ULong](#px_ulong)|**ULONG** 형식의 컨트롤 속성을 교환 합니다.|
|[PX_UShort](#px_ushort)|**USHORT** 형식의 컨트롤 속성을 교환 합니다.|
|[PXstring](#px_string)|문자열 컨트롤 속성을 교환 합니다.|
|[PX_VBXFontConvert](#px_vbxfontconvert)|VBX 컨트롤의 글꼴 관련 속성을 OLE 컨트롤 글꼴 속성으로 교환 합니다.|

또한 `AfxOleTypeMatchGuid` TYPEDESC와 지정 된 GUID 사이에 일치 하는 항목을 테스트 하기 위해 전역 함수가 제공 됩니다.

## <a name="px_blob"></a><a name="px_blob"></a> PX_Blob

컨트롤의 멤버 함수 내에서이 함수 `DoPropExchange` 를 호출 하 여 BLOB (binary large object) 데이터를 저장 하는 속성을 직렬화 하거나 초기화 합니다.

```cpp
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*hBlob*<br/>
속성이 저장 된 변수 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

*hBlobDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값을 적절 하 게 *Hblob* 에서 참조 하는 변수에서 읽거나 씁니다. 처음으로를 호출 하기 전에이 변수를 NULL로 초기화 해야 합니다 `PX_Blob` . 일반적으로이 작업은 컨트롤의 생성자에서 수행할 수 있습니다. *Hblobdefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 초기화 또는 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

*Hblob* 및 *hblobdefault* 핸들은 다음을 포함 하는 메모리 블록을 참조 합니다.

- 다음에 오는 이진 데이터의 길이 (바이트)를 포함 하는 DWORD입니다.

- 실제 이진 데이터를 포함 하는 메모리 블록입니다.

`PX_Blob`에서는 BLOB 형식 속성을 로드할 때 Windows [globalalloc](/windows/win32/api/winbase/nf-winbase-globalalloc) API를 사용하여 메모리를 할당합니다. 이 메모리를 확보 해야 합니다. 따라서 컨트롤의 소멸자는 모든 BLOB 형식 속성 핸들에서 [Globalfree](/windows/win32/api/winbase/nf-winbase-globalfree) 를 호출 하 여 컨트롤에 할당 된 메모리를 확보 해야 합니다.

## <a name="px_bool"></a><a name="px_bool"></a> PX_Bool

`DoPropExchange`BOOL 형식의 속성을 serialize 하거나 초기화 하려면 컨트롤의 멤버 함수 내에서이 함수를 호출 합니다.

```cpp
BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue);

BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue,
    BOOL bDefault);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*되며 bvalue*<br/>
속성이 저장 된 변수 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

*bDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값은 *Bvalue* 에서 참조 하는 변수에서 읽거나 적절 하 게 기록 됩니다. *Bdefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

## <a name="px_color"></a><a name="px_color"></a> PX_Color

`DoPropExchange`OLE_COLOR 형식의 속성을 serialize 하거나 초기화 하려면 컨트롤의 멤버 함수 내에서이 함수를 호출 합니다.

```cpp
BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue,
    OLE_COLOR clrDefault);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*clrValue*<br/>
속성이 저장 된 변수 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

*clrDefault*<br/>
컨트롤 개발자가 정의한 속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값은 적절 하 게 *Clrvalue* 에서 참조 하는 변수에 읽거나 기록 됩니다. *Clrdefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

## <a name="px_currency"></a><a name="px_currency"></a> PX_Currency

컨트롤의 멤버 함수 내에서이 함수 `DoPropExchange` 를 호출 하 여 **currency** 형식의 속성을 serialize 또는 초기화 합니다.

```cpp
BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue);

BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue,
    CY cyDefault);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*cyValue*<br/>
속성이 저장 된 변수 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

*cyDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값은 *cyValue* 에서 참조 하는 변수에서 읽거나 적절 하 게 기록 됩니다. *CyDefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

## <a name="px_datapath"></a><a name="px_datapath"></a> PX_DataPath

[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) 형식의 데이터 경로 속성을 serialize 하거나 초기화하려면 컨트롤의 `DoPropExchange` 멤버 함수 내에서 이 함수를 호출합니다.

```cpp
BOOL PX_DataPath(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CDataPathProperty& dataPathProperty);

BOOL PX_DataPath(
    CPropExchange* pPX,
    CDataPathProperty& dataPathProperty);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*dataPathProperty*<br/>
속성이 저장 된 변수 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

데이터 경로 속성은 비동기 컨트롤 속성을 구현 합니다. 속성의 값은 *dataPathProperty* 에서 참조 하는 변수에서 읽거나 적절 하 게 기록 됩니다.

## <a name="px_double"></a><a name="px_double"></a> PX_Double

`DoPropExchange`형식의 속성을 serialize 하거나 초기화 하려면 컨트롤의 멤버 함수 내에서이 함수를 호출 합니다 **`double`** .

```cpp
BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue);

BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue,
    double doubleDefault);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*doubleValue*<br/>
속성이 저장 된 변수 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

*doubleDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값은 *doubleValue* 에서 참조 하는 변수에서 읽거나 적절 하 게 기록 됩니다. *DoubleDefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

## <a name="px_font"></a><a name="px_font"></a> PX_Font

컨트롤의 멤버 함수 내에서이 함수 `DoPropExchange` 를 호출 하 여 font 형식의 속성을 serialize 또는 초기화 합니다.

```cpp
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*굵게*<br/>
`CFontHolder`글꼴 속성을 포함 하는 개체에 대 한 참조입니다.

*pFontDesc*<br/>
`FONTDESC` *PFONTDISPAMBIENT* 가 NULL 인 경우 font 속성의 기본 상태를 초기화 하는 데 사용할 값을 포함 하는 구조체에 대 한 포인터입니다.

*pFontDispAmbient*<br/>
`IFontDisp`글꼴 속성의 기본 상태를 초기화 하는 데 사용할 글꼴의 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값은 해당 하는 `font` 경우 참조에서 읽거나 씁니다 `CFontHolder` . *Pfontdesc* 및 *pFontDispAmbient* 가 지정 된 경우 필요한 경우 속성의 기본값을 초기화 하는 데 사용 됩니다. 이러한 값은 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우에 사용 됩니다. 일반적으로 *P글꼴 desc* 에 대해 NULL을 전달 하 고 `COleControl::AmbientFont` *pFontDispAmbient* 에 대해에서 반환 된 앰비언트 값을 전달 합니다. 에서 반환 되는 글꼴 개체는 `COleControl::AmbientFont` 멤버 함수를 호출 하 여 해제 해야 합니다 `IFontDisp::Release` .

## <a name="px_float"></a><a name="px_float"></a> PX_Float

`DoPropExchange`형식의 속성을 serialize 하거나 초기화 하려면 컨트롤의 멤버 함수 내에서이 함수를 호출 합니다 **`float`** .

```cpp
BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue);

BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue,
    float floatDefault);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*floatValue*<br/>
속성이 저장 된 변수 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

*floatDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값은 *floatValue* 에서 참조 하는 변수에서 읽거나 적절 하 게 기록 됩니다. *FloatDefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

## <a name="px_iunknown"></a><a name="px_iunknown"></a> PX_IUnknown

`DoPropExchange`파생 인터페이스가 있는 개체로 표시 되는 속성을 serialize 하거나 초기화 하려면 컨트롤의 멤버 함수 내에서이 함수를 호출 `IUnknown` 합니다.

```cpp
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*pUnk*<br/>
속성의 값을 나타내는 개체의 인터페이스를 포함 하는 변수에 대 한 참조입니다.

*iid*<br/>
컨트롤에서 사용 하는 속성 개체의 인터페이스를 나타내는 인터페이스 ID입니다.

*pUnkDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값은 *pUnk* 에서 참조 하는 변수에서 읽거나 적절 하 게 기록 됩니다. *PUnkDefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

## <a name="px_long"></a><a name="px_long"></a> PX_Long

`DoPropExchange`형식의 속성을 serialize 하거나 초기화 하려면 컨트롤의 멤버 함수 내에서이 함수를 호출 합니다 **`long`** .

```cpp
BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue);

BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue,
    long lDefault);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*lValue*<br/>
속성이 저장 된 변수 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

*lDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값을 적절 하 게 *lValue* 에서 참조 하는 변수에서 읽거나 씁니다. *Ldefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

## <a name="px_picture"></a><a name="px_picture"></a> PX_Picture

컨트롤의 멤버 함수 내에서이 함수 `DoPropExchange` 를 호출 하 여 컨트롤의 그림 속성을 serialize 또는 초기화 합니다.

```cpp
BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict);

BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict,
    CPictureHolder& pictDefault);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*pict*<br/>
속성이 저장 된 [Cpictureholder](../../mfc/reference/cpictureholder-class.md) 개체 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

*pictDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

적절 한 경우에는 *pict* 에서 참조 하는 변수에서 속성의 값을 읽거나 씁니다. *PictDefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

## <a name="px_short"></a><a name="px_short"></a> PX_Short

`DoPropExchange`형식의 속성을 serialize 하거나 초기화 하려면 컨트롤의 멤버 함수 내에서이 함수를 호출 합니다 **`short`** .

```cpp
BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue);

BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue,
    short sDefault);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*sValue*<br/>
속성이 저장 된 변수 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

*sDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값은 *sValue* 에서 참조 하는 변수에서 읽거나 적절 하 게 기록 됩니다. *Sdefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

## <a name="px_ulong"></a><a name="px_ulong"></a> PX_ULong

컨트롤의 멤버 함수 내에서이 함수 `DoPropExchange` 를 호출 하 여 **ULONG** 형식의 속성을 serialize 또는 초기화 합니다.

```cpp
BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue);

BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue,
    long ulDefault);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*ulValue*<br/>
속성이 저장 된 변수 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

*ulDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값은 *Ulvalue* 에서 참조 하는 변수에서 적절 하 게 읽거나 씁니다. *Uldefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

## <a name="px_ushort"></a><a name="px_ushort"></a> PX_UShort

`DoPropExchange`형식의 속성을 serialize 하거나 초기화 하려면 컨트롤의 멤버 함수 내에서이 함수를 호출 합니다 **`unsigned short`** .

```cpp
BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue);

BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue,
    USHORT usDefault);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*usValue*<br/>
속성이 저장 된 변수 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

*usDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값을 적절 하 게 *Usvalue* 에서 참조 하는 변수에 읽거나 씁니다. *Usdefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

## <a name="pxstring"></a><a name="px_string"></a> PXstring

컨트롤의 멤버 함수 내에서이 함수 `DoPropExchange` 를 호출 하 여 문자열 속성을 serialize 또는 초기화 합니다.

```cpp
BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue);

BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue,
    CString strDefault);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*pszPropName*<br/>
교환 되는 속성의 이름입니다.

*strValue*<br/>
속성이 저장 된 변수 (일반적으로 클래스의 멤버 변수)에 대 한 참조입니다.

*strDefault*<br/>
속성의 기본값입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

속성의 값은 *Strvalue* 에서 참조 하는 변수를 적절 하 게 읽거나 씁니다. *Strdefault* 를 지정 하면 속성의 기본값으로 사용 됩니다. 어떤 이유로 든 컨트롤의 serialization 프로세스가 실패 하는 경우이 값이 사용 됩니다.

## <a name="px_vbxfontconvert"></a><a name="px_vbxfontconvert"></a> PX_VBXFontConvert

`DoPropExchange`VBX 컨트롤의 글꼴 관련 속성을 변환 하 여 글꼴 속성을 초기화 하려면 컨트롤의 멤버 함수 내에서이 함수를 호출 합니다.

```cpp
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>매개 변수

*pPX*<br/>
[Cpropexchange](../../mfc/reference/cpropexchange-class.md) 개체 (일반적으로에 매개 변수로 전달 됨)에 대 한 포인터 `DoPropExchange` 입니다.

*굵게*<br/>
변환 된 VBX 글꼴 관련 속성을 포함 하는 OLE 컨트롤의 font 속성입니다.

### <a name="return-value"></a>반환 값

교환이 성공 하면 0이 아닌 값입니다. 실패 한 경우 0입니다.

### <a name="remarks"></a>설명

이 함수는 VBX 컨트롤에 대 한 직접 대체로 디자인 된 OLE 컨트롤 에서만 사용 해야 합니다. Visual Basic 개발 환경에서 VBX 컨트롤이 포함 된 폼을 변환 하 여 해당 하는 대체 OLE 컨트롤을 사용 하는 경우 `IDataObject::SetData` VBX 컨트롤의 속성 데이터를 포함 하는 속성 집합을 전달 하 여 컨트롤의 함수를 호출 합니다. 이 작업을 수행 하면 컨트롤의 `DoPropExchange` 함수가 호출 됩니다. `DoPropExchange` 는 `PX_VBXFontConvert` 를 호출 하 여 VBX 컨트롤의 글꼴 관련 속성 (예: "FontName", "FontSize" 등)을 OLE 컨트롤의 font 속성의 해당 구성 요소로 변환할 수 있습니다.

`PX_VBXFontConvert` 컨트롤이 실제로 VBX 폼 응용 프로그램에서 변환 되는 경우에만 호출 해야 합니다. 예를 들어:

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
