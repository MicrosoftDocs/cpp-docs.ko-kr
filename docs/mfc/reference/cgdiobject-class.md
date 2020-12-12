---
description: '자세히 알아보기: CGdiObject 클래스'
title: CGdiObject 클래스
ms.date: 11/04/2016
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
ms.openlocfilehash: a6a3d783dbfb7c25c63739330045151670208ebb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184168"
---
# <a name="cgdiobject-class"></a>CGdiObject 클래스

비트맵, 영역, 브러시, 펜, 색상표와 글꼴 등 다양한 Windows GDI(그래픽 디바이스 인터페이스) 개체에 기본 클래스를 제공합니다.

## <a name="syntax"></a>구문

```
class CGdiObject : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|`CGdiObject` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CGdiObject:: Attach](#attach)|Windows GDI 개체를 개체에 연결 `CGdiObject` 합니다.|
|[CGdiObject:: CreateStockObject](#createstockobject)|미리 정의 된 Windows 스톡 펜, 브러시 또는 글꼴 중 하나에 대 한 핸들을 검색 합니다.|
|[CGdiObject::D eleteObject](#deleteobject)|`CGdiObject`개체와 연결 된 모든 시스템 저장소를 해제 하 여 메모리에서 개체에 연결 된 WINDOWS GDI 개체를 삭제 합니다.|
|[CGdiObject::D eleteTempMap](#deletetempmap)|에서 만든 임시 개체를 모두 삭제 `CGdiObject` `FromHandle` 합니다.|
|[CGdiObject::D etach](#detach)|Windows GDI 개체를 개체에서 분리 `CGdiObject` 하 고 WINDOWS gdi 개체에 대 한 핸들을 반환 합니다.|
|[CGdiObject:: FromHandle](#fromhandle)|`CGdiObject`WINDOWS GDI 개체에 대 한 핸들을 지정 하 여 개체에 대 한 포인터를 반환 합니다.|
|[CGdiObject:: GetObject](#getobject)|개체에 연결 된 Windows GDI 개체를 설명 하는 데이터로 버퍼를 채웁니다 `CGdiObject` .|
|[CGdiObject:: GetObjectType](#getobjecttype)|GDI 개체의 형식을 검색 합니다.|
|[CGdiObject:: GetSafeHandle](#getsafehandle)|`m_hObject` **`this`** 가 null이 아닌 경우를 반환 합니다 .이 경우 null이 반환 됩니다.|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|브러시의 원점을 다시 설정 하거나 논리 색상표를 다시 설정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CGdiObject:: operator! =](#operator_neq)|두 GDI 개체가 논리적으로 같지 않은 지 여부를 확인 합니다.|
|[CGdiObject:: operator = =](#operator_eq_eq)|두 GDI 개체가 논리적으로 같은지 여부를 확인 합니다.|
|[CGdiObject:: operator HGDIOBJ](#operator_hgdiobj)|연결 된 Windows GDI 개체에 대 한 핸들을 검색 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CGdiObject:: m_hObject](#m_hobject)|이 개체에 연결 된 HBITMAP, HPALETTE, HRGN, HPALETTE, HPALETTE 또는 HPALETTE를 포함 하는 핸들입니다.|

## <a name="remarks"></a>설명

을 직접 만들지는 않습니다 `CGdiObject` . 대신, 또는와 같은 파생 클래스 중 하나에서 개체를 만듭니다 `CPen` `CBrush` .

에 대 한 자세한 내용은 `CGdiObject` [그래픽 개체](../../mfc/graphic-objects.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cgdiobjectattach"></a><a name="attach"></a> CGdiObject:: Attach

Windows GDI 개체를 개체에 연결 `CGdiObject` 합니다.

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>매개 변수

*hObject*<br/>
Windows GDI 개체 (예: HPEN 또는 HPEN)에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

첨부 파일이 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="cgdiobjectcgdiobject"></a><a name="cgdiobject"></a> CGdiObject::CGdiObject

`CGdiObject` 개체를 생성합니다.

```
CGdiObject();
```

### <a name="remarks"></a>설명

을 직접 만들지는 않습니다 `CGdiObject` . 대신, 또는와 같은 파생 클래스 중 하나에서 개체를 만듭니다 `CPen` `Cbrush` .

## <a name="cgdiobjectcreatestockobject"></a><a name="createstockobject"></a> CGdiObject:: CreateStockObject

미리 정의 된 스톡 Windows GDI 펜, 브러시 또는 글꼴 중 하나에 대 한 핸들을 검색 하 고 개체에 GDI 개체를 연결 합니다 `CGdiObject` .

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
원하는 스톡 개체의 형식을 지정 하는 상수입니다. 적절 한 값에 대 한 설명은 Windows SDK의 [GetStockObject](/windows/win32/api/wingdi/nf-wingdi-getstockobject) 에 대 한 *fnObject* 매개 변수를 참조 하세요.

### <a name="return-value"></a>반환 값

함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

스톡 펜의 경우와 같이 Windows GDI 개체 형식에 해당 하는 파생 클래스 중 하나를 사용 하 여이 함수를 호출 `CPen` 합니다.

## <a name="cgdiobjectdeleteobject"></a><a name="deleteobject"></a> CGdiObject::D eleteObject

Windows GDI 개체와 연결 된 모든 시스템 저장소를 해제 하 여 메모리에서 연결 된 Windows GDI 개체를 삭제 합니다.

```
BOOL DeleteObject();
```

### <a name="return-value"></a>반환 값

GDI 개체가 성공적으로 삭제 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

개체와 연결 된 저장소는 `CGdiObject` 이 호출의 영향을 받지 않습니다. 응용 프로그램은 `DeleteObject` `CGdiObject` 현재 장치 컨텍스트로 선택 된 개체에서를 호출 하면 안 됩니다.

패턴 브러시가 삭제 되 면 브러시와 연결 된 비트맵이 삭제 되지 않습니다. 비트맵은 독립적으로 삭제 해야 합니다.

## <a name="cgdiobjectdeletetempmap"></a><a name="deletetempmap"></a> CGdiObject::D eleteTempMap

유휴 시간 처리기에 의해 자동으로 호출 `CWinApp` 되어 `DeleteTempMap` 에서 만든 임시 개체를 모두 삭제 `CGdiObject` `FromHandle` 합니다.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>설명

`DeleteTempMap` 개체를 삭제 하기 전에 임시 개체에 연결 된 Windows GDI 개체를 분리 `CGdiObject` `CGdiObject` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

## <a name="cgdiobjectdetach"></a><a name="detach"></a> CGdiObject::D etach

Windows GDI 개체를 개체에서 분리 `CGdiObject` 하 고 WINDOWS gdi 개체에 대 한 핸들을 반환 합니다.

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>반환 값

`HANDLE`WINDOWS gdi 개체가 분리 되 면이 고, 연결 된 gdi 개체가 없으면 NULL입니다.

## <a name="cgdiobjectfromhandle"></a><a name="fromhandle"></a> CGdiObject:: FromHandle

`CGdiObject`WINDOWS GDI 개체에 대 한 핸들을 지정 하 여 개체에 대 한 포인터를 반환 합니다.

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>매개 변수

*hObject*<br/>
Windows GDI 개체에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

`CGdiObject`일시적 이거나 영구적 일 수 있는에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`CGdiObject`개체가 WINDOWS GDI 개체에 아직 연결 되지 않은 경우 임시 `CGdiObject` 개체가 생성 되 고 연결 됩니다.

이 임시 `CGdiObject` 개체는 다음에 응용 프로그램이 이벤트 루프에서 유휴 시간을 초과할 때까지 유효 합니다 .이 경우 모든 임시 그래픽 개체가 삭제 됩니다. 이에 대 한 또 다른 방법은 임시 개체가 하나의 창 메시지를 처리 하는 동안에만 유효 하다는 것입니다.

## <a name="cgdiobjectgetobject"></a><a name="getobject"></a> CGdiObject:: GetObject

지정 된 개체를 정의 하는 데이터로 버퍼를 채웁니다.

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>매개 변수

*nCount*<br/>
*LpObject* 버퍼로 복사할 바이트 수를 지정 합니다.

*lpObject*<br/>
정보를 받을 사용자 제공 버퍼를 가리킵니다.

### <a name="return-value"></a>반환 값

검색 된 바이트 수입니다. 오류가 발생 하면 0이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

함수는 다음 목록과 같이 그래픽 개체의 형식에 따라 형식이 결정 되는 데이터 구조를 검색 합니다.

|개체|버퍼 유형|
|------------|-----------------|
|`CPen`|[LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[비트맵이](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|지원되지 않음|

개체가 개체인 경우는 `CBitmap` `GetObject` 비트맵의 너비, 높이 및 색 형식 정보만 반환 합니다. [Cbitmap:: GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits)를 사용 하 여 실제 비트를 검색할 수 있습니다.

개체가 `CPalette` 개체 이면 `GetObject` 색상표에 있는 항목 수를 지정 하는 단어를 검색 합니다. 함수는 색상표를 정의 하는 [Logpalette](/windows/win32/api/wingdi/ns-wingdi-logpalette) 구조를 검색 하지 않습니다. 응용 프로그램은 [Cpalette:: GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries)를 호출 하 여 색상표 항목에 대 한 정보를 가져올 수 있습니다.

## <a name="cgdiobjectgetobjecttype"></a><a name="getobjecttype"></a> CGdiObject:: GetObjectType

GDI 개체의 형식을 검색 합니다.

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>반환 값

성공 하는 경우 개체의 형식입니다. 그렇지 않으면 0입니다. 값은 다음 중 하나일 수 있습니다.

- OBJ_BITMAP 비트맵

- OBJ_BRUSH 브러시

- OBJ_FONT 글꼴

- OBJ_PAL 팔레트

- OBJ_PEN 펜

- OBJ_EXTPEN 확장 된 펜

- OBJ_REGION 지역

- OBJ_DC 장치 컨텍스트

- OBJ_MEMDC 메모리 장치 컨텍스트

- 메타 파일 OBJ_METAFILE

- OBJ_METADC 메타 파일 장치 컨텍스트

- 확장 메타 파일 OBJ_ENHMETAFILE

- OBJ_ENHMETADC 향상 된 메타 파일 장치 컨텍스트

## <a name="cgdiobjectgetsafehandle"></a><a name="getsafehandle"></a> CGdiObject:: GetSafeHandle

`m_hObject` **`this`** 가 null이 아닌 경우를 반환 합니다 .이 경우 null이 반환 됩니다.

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>반환 값

연결 된 Windows GDI 개체에 대 한 핸들입니다. 개체가 연결 되어 있지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이는 일반 핸들 인터페이스 패러다임의 일부 이며 NULL이 핸들에 대 한 유효한 값 또는 특수 값인 경우에 유용 합니다.

### <a name="example"></a>예제

  [CWnd:: IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled)의 예제를 참조 하세요.

## <a name="cgdiobjectm_hobject"></a><a name="m_hobject"></a> CGdiObject:: m_hObject

이 개체에 연결 된 HBITMAP, HRGN, HBRUSH, HBRUSH, HBRUSH 또는 HBRUSH를 포함 하는 핸들입니다.

```
HGDIOBJ m_hObject;
```

## <a name="cgdiobjectoperator-"></a><a name="operator_neq"></a> CGdiObject:: operator! =

두 GDI 개체가 논리적으로 같지 않은 지 여부를 확인 합니다.

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>매개 변수

*obj*<br/>
기존에 대 한 포인터 `CGdiObject` 입니다.

### <a name="remarks"></a>설명

좌 변에 있는 GDI 개체가 우변에 있는 GDI 개체와 같지 않은 지 여부를 확인 합니다.

## <a name="cgdiobjectoperator-"></a><a name="operator_eq_eq"></a> CGdiObject:: operator = =

두 GDI 개체가 논리적으로 같은지 여부를 확인 합니다.

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>매개 변수

*obj*<br/>
기존에 대 한 참조 `CGdiObject` 입니다.

### <a name="remarks"></a>설명

좌 변에 있는 GDI 개체가 우변에 있는 GDI 개체와 같은지 여부를 확인 합니다.

## <a name="cgdiobjectoperator-hgdiobj"></a><a name="operator_hgdiobj"></a> CGdiObject:: operator HGDIOBJ

연결 된 Windows GDI 개체에 대 한 핸들을 검색 합니다. 개체가 연결 되어 있지 않으면 NULL입니다.

```
operator HGDIOBJ() const;
```

## <a name="cgdiobjectunrealizeobject"></a><a name="unrealizeobject"></a> CGdiObject::UnrealizeObject

브러시의 원점을 다시 설정 하거나 논리 색상표를 다시 설정 합니다.

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`UnrealizeObject`는 클래스의 멤버 함수 이지만 `CGdiObject` 또는 개체 에서만 호출 되어야 합니다 `CBrush` `CPalette` .

`CBrush`개체의 경우는 다음에 `UnrealizeObject` 장치 컨텍스트로 선택 될 때 지정 된 브러시의 원본을 다시 설정 하도록 시스템에 지시 합니다. 개체가 개체인 경우는 `CPalette` `UnrealizeObject` 이전에 실현 되지 않은 것 처럼 팔레트를 인식 하도록 시스템에 지시 합니다. 다음 번에 응용 프로그램이 지정 된 색상표에 대해 [CDC:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) 함수를 호출 하면 시스템에서 논리 색상표를 시스템 색상표로 완전히 다시 매핑합니다.

`UnrealizeObject`함수는 스톡 개체와 함께 사용 하면 안 됩니다. `UnrealizeObject`새 브러시 원본이 설정 될 때마다 ( [CDC:: SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) 함수를 통해) 함수를 호출 해야 합니다. `UnrealizeObject`현재 선택한 브러시 나 표시 컨텍스트의 현재 선택 된 색상표에 대해서는 함수를 호출 하면 안 됩니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 클래스](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush 클래스](../../mfc/reference/cbrush-class.md)<br/>
[CFont 클래스](../../mfc/reference/cfont-class.md)<br/>
[CPalette 클래스](../../mfc/reference/cpalette-class.md)<br/>
[CPen 클래스](../../mfc/reference/cpen-class.md)<br/>
[CRgn 클래스](../../mfc/reference/crgn-class.md)
