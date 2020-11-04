---
title: CBitmap 클래스
ms.date: 11/04/2016
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
ms.openlocfilehash: 8c19a54584390312cfd1657e88898cdb044179d0
ms.sourcegitcommit: d77159732a8e782b2a1b7abea552065f2b6f61c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344581"
---
# <a name="cbitmap-class"></a>CBitmap 클래스

Windows GDI(그래픽 디바이스 인터페이스) 비트맵을 캡슐화하고 비트맵을 조작하는 멤버 함수를 제공합니다.

## <a name="syntax"></a>구문

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|Description|
|----------|-----------------|
|[CBitmap:: CBitmap](#cbitmap)|`CBitmap` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|Description|
|----------|-----------------|
|[CBitmap:: CreateBitmap](#createbitmap)|지정 된 너비, 높이 및 비트 패턴이 있는 장치 종속 메모리 비트맵을 사용 하 여 개체를 초기화 합니다.|
|[CBitmap:: CreateBitmapIndirect](#createbitmapindirect)|구조체에 지정 된 너비, 높이 및 비트 패턴의 비트맵 (지정 된 경우)을 사용 하 여 개체를 초기화 `BITMAP` 합니다.|
|[CBitmap:: CreateCompatibleBitmap](#createcompatiblebitmap)|지정 된 장치와 호환 되도록 비트맵을 사용 하 여 개체를 초기화 합니다.|
|[CBitmap:: CreateDiscardableBitmap](#creatediscardablebitmap)|지정 된 장치와 호환 되는 삭제 가능한 비트맵을 사용 하 여 개체를 초기화 합니다.|
|[CBitmap:: FromHandle](#fromhandle)|`CBitmap`Windows 비트맵 핸들을 지정 하면 개체에 대 한 포인터를 반환 `HBITMAP` 합니다.|
|[CBitmap:: GetBitmap](#getbitmap)|`BITMAP`비트맵에 대 한 정보를 사용 하 여 구조체를 채웁니다.|
|[CBitmap:: GetBitmapBits](#getbitmapbits)|지정 된 비트맵의 비트를 지정 된 버퍼에 복사 합니다.|
|[CBitmap:: GetBitmapDimension](#getbitmapdimension)|비트맵의 너비와 높이를 반환 합니다. 높이 및 너비는 이전에 [SetBitmapDimension](#setbitmapdimension) 멤버 함수에 의해 설정 된 것으로 간주 됩니다.|
|[CBitmap:: LoadBitmap](#loadbitmap)|응용 프로그램의 실행 파일에서 명명 된 비트맵 리소스를 로드 하 고 개체에 비트맵을 연결 하 여 개체를 초기화 합니다.|
|[CBitmap:: LoadMappedBitmap](#loadmappedbitmap)|비트맵을 로드 하 고 색을 현재 시스템 색에 매핑합니다.|
|[CBitmap:: LoadOEMBitmap](#loadoembitmap)|미리 정의 된 Windows 비트맵을 로드 하 고 비트맵을 개체에 연결 하 여 개체를 초기화 합니다.|
|[CBitmap:: SetBitmapBits](#setbitmapbits)|비트맵의 비트를 지정 된 비트 값으로 설정 합니다.|
|[CBitmap:: SetBitmapDimension](#setbitmapdimension)|0.1 밀리미터 단위의 비트맵에 너비와 높이를 할당 합니다.|

### <a name="public-operators"></a>Public 연산자

|이름|Description|
|----------|-----------------|
|[CBitmap:: operator HBITMAP](#operator_hbitmap)|개체에 연결 된 Windows 핸들을 반환 합니다 `CBitmap` .|

## <a name="remarks"></a>설명

개체를 사용 하려면 개체를 생성 하 고, `CBitmap` 초기화 멤버 함수 중 하나를 사용 하 여 비트맵 핸들을 해당 개체에 연결 하 고, 개체의 멤버 함수를 호출 합니다.

와 같은 그래픽 개체를 사용 하는 방법에 대 한 자세한 내용은 `CBitmap` [그래픽 개체](../../mfc/graphic-objects.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cbitmapcbitmap"></a><a name="cbitmap"></a> CBitmap:: CBitmap

`CBitmap` 개체를 생성합니다.

```
CBitmap();
```

### <a name="remarks"></a>설명

결과 개체는 초기화 멤버 함수 중 하나를 사용 하 여 초기화 해야 합니다.

## <a name="cbitmapcreatebitmap"></a><a name="createbitmap"></a> CBitmap:: CreateBitmap

너비, 높이 및 비트 패턴이 지정되어 있는 디바이스 종속적 메모리 비트맵을 초기화합니다.

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>매개 변수

*nWidth*<br/>
비트맵의 너비(픽셀)를 지정합니다.

*nHeight*<br/>
비트맵의 높이(픽셀)를 지정합니다.

*nPlanes*<br/>
비트맵에서 색 평면의 수를 지정합니다.

*nBitcount*<br/>
표시 픽셀당 색 비트의 수를 지정합니다.

*lpBits*<br/>
초기 비트맵 비트 값이 포함된 바이트 배열을 가리킵니다. NULL이면 새 비트맵이 초기화되어 있지 않습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

색 비트맵의 경우 *Nplanes* 나 *nbitcount* 매개 변수를 1로 설정 해야 합니다. 이러한 매개 변수가 둘 다 1로 설정되면 `CreateBitmap` 은 단색 비트맵을 만듭니다.

디스플레이 디바이스에 대한 비트맵을 직접 선택할 수는 없지만 [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) 를 사용하여 “메모리 디바이스 컨텍스트"에 대한 현재 비트맵을 선택하고 [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) 함수를 사용하여 호환되는 디바이스 컨텍스트에 복사할 수 있습니다.

`CBitmap` 함수에서 만들어진 `CreateBitmap` 개체 사용을 완료하면 먼저 디바이스 컨텍스트에서 비트맵을 선택하고 나서 `CBitmap` 개체를 삭제합니다.

자세한 내용은 구조체의 필드에 대 한 설명을 참조 하세요 `bmBits` `BITMAP` . [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) 구조체는 [CBitmap::CreateBitmapIndirect](#createbitmapindirect) 멤버 함수에서 설명합니다.

## <a name="cbitmapcreatebitmapindirect"></a><a name="createbitmapindirect"></a> CBitmap:: CreateBitmapIndirect

*Lpbitmap* 에서 가리키는 구조에 지정 된 너비, 높이 및 비트 패턴 (지정 된 경우)이 있는 비트맵을 초기화 합니다.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>매개 변수

*lpBitmap*<br/>
비트맵에 대 한 정보를 포함 하는 [비트맵](/windows/win32/api/wingdi/ns-wingdi-bitmap) 구조를 가리킵니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

디스플레이 장치에 대해 비트맵을 직접 선택할 수는 없지만 cdc: [: SelectObject](../../mfc/reference/cdc-class.md#selectobject) 를 사용 하 고 cdc:: [BitBlt](../../mfc/reference/cdc-class.md#bitblt) 또는 [cdc:: StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) 함수를 사용 하 여 호환 되는 장치 컨텍스트에 복사 하 여 메모리 장치 컨텍스트의 현재 비트맵으로 선택할 수 있습니다. [CDC::P atblt](../../mfc/reference/cdc-class.md#patblt) 함수는 현재 브러시의 비트맵을 디스플레이 장치 컨텍스트에 직접 복사할 수 있습니다.

`BITMAP` *Lpbitmap* 매개 변수에서 가리키는 구조가 함수를 사용 하 여 채워진 경우 `GetObject` 비트맵의 비트가 지정 되지 않고 비트맵이 초기화 되지 않습니다. 비트맵을 초기화 하기 위해 응용 프로그램은 [CDC:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) 또는 [setdibits](/windows/win32/api/wingdi/nf-wingdi-setdibits) 와 같은 함수를 사용 하 여의 첫 번째 매개 변수로 식별 되는 비트맵에서 `CGdiObject::GetObject` 로 만든 비트맵으로 비트를 복사할 수 있습니다 `CreateBitmapIndirect` .

함수를 사용 하 여 `CBitmap` 만든 개체를 마치면 `CreateBitmapIndirect` 먼저 장치 컨텍스트에서 비트맵을 선택 하 고 개체를 삭제 `CBitmap` 합니다.

## <a name="cbitmapcreatecompatiblebitmap"></a><a name="createcompatiblebitmap"></a> CBitmap:: CreateCompatibleBitmap

*PDC* 로 지정 된 장치와 호환 되는 비트맵을 초기화 합니다.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
장치 컨텍스트를 지정 합니다.

*nWidth*<br/>
비트맵의 너비(픽셀)를 지정합니다.

*nHeight*<br/>
비트맵의 높이(픽셀)를 지정합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

비트맵에 지정 된 장치 컨텍스트와 동일한 수의 색 평면 또는 픽셀 당 비트 형식이 있습니다. *PDC* 에서 지정한 것과 호환 되는 모든 메모리 장치에 대 한 현재 비트맵으로 선택할 수 있습니다.

*PDC* 가 메모리 장치 컨텍스트인 경우 반환 된 비트맵은 해당 장치 컨텍스트에서 현재 선택 된 비트맵과 동일한 형식입니다. "메모리 장치 컨텍스트"는 표시 표면을 나타내는 메모리 블록입니다. 이를 사용 하 여 메모리에서 이미지를 준비 하 고 호환 장치의 실제 표시 화면에 복사할 수 있습니다.

메모리 장치 컨텍스트를 만들면 GDI에서 자동으로 흑백 스톡 비트맵을 선택 합니다.

색 메모리 장치 컨텍스트는 색 또는 단색 비트맵을 선택 하 여 사용할 수 있으므로, 함수에서 반환 하는 비트맵의 형식은 `CreateCompatibleBitmap` 항상 동일 하지는 않습니다. 그러나 비 메모리 장치 컨텍스트에 대 한 호환 비트맵의 형식은 항상 장치의 형식입니다.

`CBitmap`함수를 사용 하 여 만든 개체를 마치면 `CreateCompatibleBitmap` 먼저 장치 컨텍스트에서 비트맵을 선택 하 고 개체를 삭제 `CBitmap` 합니다.

## <a name="cbitmapcreatediscardablebitmap"></a><a name="creatediscardablebitmap"></a> CBitmap:: CreateDiscardableBitmap

*PDC* 로 식별 되는 장치 컨텍스트와 호환 되는 삭제 가능한 비트맵을 초기화 합니다.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
장치 컨텍스트를 지정 합니다.

*nWidth*<br/>
비트맵의 너비 (비트)를 지정 합니다.

*nHeight*<br/>
비트맵의 높이 (비트)를 지정 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

비트맵에 지정 된 장치 컨텍스트와 동일한 수의 색 평면 또는 픽셀 당 비트 형식이 있습니다. 응용 프로그램은이 비트맵을 *pDC* 에서 지정한 것과 호환 되는 메모리 장치에 대 한 현재 비트맵으로 선택할 수 있습니다.

응용 프로그램에서이 함수를 통해 생성 된 비트맵이 표시 컨텍스트로 선택 되지 않은 경우에만이 비트맵을 삭제할 수 있습니다. 선택 하지 않은 경우 Windows에서 비트맵을 삭제 하 고 나중에 응용 프로그램에서 선택 하려고 하면 [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) 함수는 NULL을 반환 합니다.

`CBitmap`함수를 사용 하 여 만든 개체를 마치면 `CreateDiscardableBitmap` 먼저 장치 컨텍스트에서 비트맵을 선택 하 고 개체를 삭제 `CBitmap` 합니다.

## <a name="cbitmapfromhandle"></a><a name="fromhandle"></a> CBitmap:: FromHandle

`CBitmap`WINDOWS GDI 비트맵 핸들을 지정 하면 개체에 대 한 포인터를 반환 합니다.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>매개 변수

*hBitmap*<br/>
Windows GDI 비트맵을 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 개체에 대 한 포인터 `CBitmap` 이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`CBitmap`개체가 핸들에 아직 연결 되지 않은 경우 임시 `CBitmap` 개체가 생성 되 고 연결 됩니다. 이 임시 `CBitmap` 개체는 다음에 응용 프로그램이 이벤트 루프에서 유휴 시간을 초과 하 여 모든 임시 그래픽 개체가 삭제 될 때 까지만 유효 합니다. 이에 대 한 또 다른 방법은 임시 개체가 하나의 창 메시지를 처리 하는 동안에만 유효 하다는 것입니다.

## <a name="cbitmapgetbitmap"></a><a name="getbitmap"></a> CBitmap:: GetBitmap

연결 된 비트맵의 이미지 속성을 검색 합니다.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>매개 변수

*pBitMap*<br/>
이미지 속성을 받는 [비트맵](/windows/win32/api/wingdi/ns-wingdi-bitmap) 구조체에 대 한 포인터입니다. 이 매개 변수는 NULL이 아니어야 합니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

## <a name="cbitmapgetbitmapbits"></a><a name="getbitmapbits"></a> CBitmap:: GetBitmapBits

연결 된 비트맵의 비트 패턴을 지정 된 버퍼에 복사 합니다.

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>매개 변수

*dwCount*<br/>
버퍼에 복사할 바이트 수입니다.

*lpBits*<br/>
비트맵을 수신 하는 버퍼에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드에 성공한 경우 버퍼에 복사 되는 바이트 수입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[Cbitmap:: GetBitmap](#getbitmap) 을 사용 하 여 필요한 버퍼 크기를 확인 합니다.

## <a name="cbitmapgetbitmapdimension"></a><a name="getbitmapdimension"></a> CBitmap:: GetBitmapDimension

비트맵의 너비와 높이를 반환 합니다.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>반환 값

비트맵의 너비와 높이 이며 0.1 밀리미터 단위로 측정 됩니다. 높이가 `cy` 개체의 멤버에 `CSize` 있고 너비는 `cx` 멤버에 있습니다. 을 사용 하 여 비트맵 너비와 높이를 설정 하지 않은 경우에는 `SetBitmapDimension` 반환 값이 0입니다.

### <a name="remarks"></a>설명

높이 및 너비는 [SetBitmapDimension](#setbitmapdimension) 멤버 함수를 사용 하 여 이전에 설정 된 것으로 간주 됩니다.

## <a name="cbitmaploadbitmap"></a><a name="loadbitmap"></a> CBitmap:: LoadBitmap

*LpszResourceName* 로 명명 된 비트맵 리소스를 로드 하거나 응용 프로그램의 실행 파일에서 *nIDResource* 의 ID 번호로 식별 합니다.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>매개 변수

*lpszResourceName*<br/>
비트맵 리소스의 이름을 포함 하는 null로 끝나는 문자열을 가리킵니다.

*nIDResource*<br/>
비트맵 리소스의 리소스 ID 번호를 지정 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

로드 된 비트맵이 개체에 연결 됩니다 `CBitmap` .

*LpszResourceName* 에 의해 식별 된 비트맵이 없거나 비트맵을 로드 하기에 메모리가 부족 한 경우이 함수는 0을 반환 합니다.

[CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) 함수를 사용 하 여 함수에서 로드 한 비트맵을 삭제할 수 있습니다 `LoadBitmap` . 그렇지 않으면 `CBitmap` 소멸자가 개체를 삭제 합니다.

> [!CAUTION]
> 개체를 삭제 하기 전에 장치 컨텍스트에서 선택 되지 않았는지 확인 합니다.

다음 비트맵이 Windows 버전 3.1 이상에 추가 되었습니다.

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

이러한 비트맵은 Windows 버전 3.0 및 이전 버전의 장치 드라이버에서 찾을 수 없습니다. 비트맵의 전체 목록과 모양을 표시 하는 방법에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

## <a name="cbitmaploadmappedbitmap"></a><a name="loadmappedbitmap"></a> CBitmap:: LoadMappedBitmap

비트맵을 로드 하 고 색을 현재 시스템 색에 매핑하려면이 멤버 함수를 호출 합니다.

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>매개 변수

*nIDBitmap*<br/>
비트맵 리소스의 ID입니다.

*nFlags*<br/>
비트맵에 대 한 플래그입니다. 0 또는 CMB_MASKED 수 있습니다.

*lpColorMap*<br/>
비트맵을 매핑하는 데 `COLORMAP` 필요한 색 정보를 포함 하는 구조체에 대 한 포인터입니다. 이 매개 변수가 NULL 이면 함수는 기본 색 맵을 사용 합니다.

*nMapSize*<br/>
*Lpcolormap* 에서 가리키는 색 맵의 수입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본적으로에서는 `LoadMappedBitmap` 단추 문자 모양에 일반적으로 사용 되는 색을 매핑합니다.

매핑된 비트맵을 만드는 방법에 대 한 자세한 내용은 Windows SDK Windows 함수 [CreateMappedBitmap](/windows/win32/api/commctrl/nf-commctrl-createmappedbitmap) 및 [colormap](/windows/win32/api/commctrl/ns-commctrl-colormap) 구조를 참조 하세요.

## <a name="cbitmaploadoembitmap"></a><a name="loadoembitmap"></a> CBitmap:: LoadOEMBitmap

Windows에서 사용 하는 미리 정의 된 비트맵을 로드 합니다.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>매개 변수

*nIDBitmap*<br/>
미리 정의 된 Windows 비트맵의 ID 번호입니다. 가능한 값은 WINDOWS에서 아래에 나열 되어 있습니다. 넣기

:::row:::
   :::column span="":::
      OBM_BTNCORNERS \
      OBM_BTSIZE \
      OBM_CHECK \
      OBM_CHECKBOXES \
      OBM_CLOSE \
      OBM_COMBO \
      OBM_DNARROW \
      OBM_DNARROWD \
      OBM_DNARROWI \
      OBM_LFARROW \
      OBM_LFARROWD \
      OBM_LFARROWI
   :::column-end:::
   :::column span="":::
      OBM_MNARROW \
      OBM_OLD_CLOSE \
      OBM_OLD_DNARROW \
      OBM_OLD_LFARROW \
      OBM_OLD_REDUCE \
      OBM_OLD_RESTORE \
      OBM_OLD_RGARROW \
      OBM_OLD_UPARROW \
      OBM_OLD_ZOOM \
      OBM_REDUCE \
      OBM_REDUCED
   :::column-end:::
   :::column span="":::
      OBM_RESTORE \
      OBM_RESTORED \
      OBM_RGARROW \
      OBM_RGARROWD \
      OBM_RGARROWI \
      OBM_SIZE \
      OBM_UPARROW \
      OBM_UPARROW \
      OBM_UPARROWD \
      OBM_ZOOM \
      OBM_ZOOMD
   :::column-end:::
:::row-end:::

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

OBM_OLD 시작 하는 비트맵 이름은 3.0 이전 Windows 버전에서 사용 하는 비트맵을 나타냅니다.

WINDOWS를 포함 하기 전에 상수 OEMRESOURCE를 정의 해야 합니다. H를 사용 하 여 **OBM_** 상수를 사용 합니다.

## <a name="cbitmapoperator-hbitmap"></a><a name="operator_hbitmap"></a> CBitmap:: operator HBITMAP

이 연산자를 사용 하 여 개체의 연결 된 Windows GDI 핸들을 가져옵니다 `CBitmap` .

```
operator HBITMAP() const;
```

### <a name="return-value"></a>반환 값

성공 하면 개체가 나타내는 Windows GDI 개체에 대 한 핸들이 고, `CBitmap` 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 연산자는 개체의 직접 사용을 지 원하는 캐스팅 연산자입니다 `HBITMAP` .

그래픽 개체를 사용 하는 방법에 대 한 자세한 내용은 Windows SDK의 [그래픽 개체](/windows/win32/gdi/graphic-objects) 를 참조 하세요.

## <a name="cbitmapsetbitmapbits"></a><a name="setbitmapbits"></a> CBitmap:: SetBitmapBits

비트맵의 비트를 *lpbits* 에서 제공 하는 비트 값으로 설정 합니다.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>매개 변수

*dwCount*<br/>
*Lpbits* 가리키는 바이트 수를 지정 합니다.

*lpBits*<br/>
개체에 복사할 픽셀 값을 포함 하는 바이트 배열을 가리킵니다 `CBitmap` . 비트맵이 이미지를 올바르게 렌더링 하려면 CBitmap 인스턴스를 만들 때 지정 된 높이, 너비 및 색 농도 값에 맞게 값의 서식을 지정 해야 합니다. 자세한 내용은 [Cbitmap:: createbitmap](#createbitmap)을 참조 하세요.

### <a name="return-value"></a>반환 값

비트맵 비트를 설정 하는 데 사용 된 바이트 수입니다. 함수가 실패 하면 0입니다.

## <a name="cbitmapsetbitmapdimension"></a><a name="setbitmapdimension"></a> CBitmap:: SetBitmapDimension

0.1 밀리미터 단위의 비트맵에 너비와 높이를 할당 합니다.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>매개 변수

*nWidth*<br/>
비트맵의 너비 (0.1-밀리미터 단위)를 지정 합니다.

*nHeight*<br/>
비트맵의 높이 (0.1 밀리미터 단위)를 지정 합니다.

### <a name="return-value"></a>반환 값

이전 비트맵 차원입니다. Height는 `cy` 개체의 멤버 변수에 `CSize` 있으며 너비는 `cx` 멤버 변수에 있습니다.

### <a name="remarks"></a>설명

GDI는 응용 프로그램이 [GetBitmapDimension](#getbitmapdimension) 멤버 함수를 호출할 때 반환 하는 경우를 제외 하 고 이러한 값을 사용 하지 않습니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 MDI](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 클래스](../../mfc/reference/cgdiobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
