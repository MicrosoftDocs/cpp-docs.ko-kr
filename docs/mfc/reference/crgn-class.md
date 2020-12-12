---
description: '자세히 알아보기: CRgn 클래스'
title: CRgn 클래스
ms.date: 11/04/2016
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
ms.openlocfilehash: 7506f7fa839c36e079ffe986052a3564ddf0169e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264858"
---
# <a name="crgn-class"></a>CRgn 클래스

Windows GDI(그래픽 디바이스 인터페이스) 영역을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CRgn : public CGdiObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CRgn::CRgn](#crgn)|`CRgn` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRgn:: CombineRgn](#combinergn)|`CRgn`지정 된 두 개체의 합집합에 해당 하는 개체를 설정 `CRgn` 합니다.|
|[CRgn:: CopyRgn](#copyrgn)|지정 된 `CRgn` 개체의 복사본 인 개체를 설정 `CRgn` 합니다.|
|[CRgn:: CreateEllipticRgn](#createellipticrgn)|`CRgn`타원형 영역을 사용 하 여 개체를 초기화 합니다.|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|[RECT](/windows/win32/api/windef/ns-windef-rect) 구조체로 정의 된 타원 영역을 사용 하 여 `CRgn`개체를 초기화합니다.|
|[CRgn:: CreateFromData](#createfromdata)|지정 된 영역 및 변환 데이터에서 영역을 만듭니다.|
|[CRgn:: CreateFromPath](#createfrompath)|지정 된 장치 컨텍스트에 선택한 경로에서 영역을 만듭니다.|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|`CRgn`다각형 영역을 사용 하 여 개체를 초기화 합니다. 필요한 경우 마지막 정점부터 첫 번째 정점까지 선을 그려 시스템에서 다각형이 자동으로 닫힙니다.|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|`CRgn`일련의 폐쇄형 다각형으로 구성 된 영역을 사용 하 여 개체를 초기화 합니다. 다각형이 분리 되어 있거나 겹칠 수 있습니다.|
|[CRgn:: CreateRectRgn](#createrectrgn)|`CRgn`사각형 영역을 사용 하 여 개체를 초기화 합니다.|
|[CRgn:: CreateRectRgnIndirect](#createrectrgnindirect)|[RECT](/windows/win32/api/windef/ns-windef-rect) 구조에서 정의된 사각형 영역을 사용하여 `CRgn` 개체를 초기화합니다.|
|[CRgn:: CreateRoundRectRgn](#createroundrectrgn)|모퉁이가 `CRgn` 둥근 사각형 영역을 사용 하 여 개체를 초기화 합니다.|
|[CRgn:: EqualRgn](#equalrgn)|두 `CRgn` 개체가 같은지 여부를 확인 합니다.|
|[CRgn:: FromHandle](#fromhandle)|`CRgn`Windows 영역에 대 한 핸들을 지정 하면 개체에 대 한 포인터를 반환 합니다.|
|[CRgn::GetRegionData](#getregiondata)|지정 된 버퍼를 지정 된 영역을 설명 하는 데이터로 채웁니다.|
|[CRgn:: GetRgnBox](#getrgnbox)|개체의 경계 사각형의 좌표를 검색 `CRgn` 합니다.|
|[CRgn::OffsetRgn](#offsetrgn)|지정 된 `CRgn` 오프셋으로 개체를 이동 합니다.|
|[CRgn::PtInRegion](#ptinregion)|지정 된 지점이 영역에 있는지 여부를 확인 합니다.|
|[CRgn::RectInRegion](#rectinregion)|지정 된 사각형의 일부가 영역의 경계 내에 있는지 여부를 확인 합니다.|
|[CRgn::SetRectRgn](#setrectrgn)|개체를 `CRgn` 지정 된 사각형 영역으로 설정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CRgn:: operator HRGN](#operator_hrgn)|개체에 포함 된 Windows 핸들을 반환 합니다 `CRgn` .|

## <a name="remarks"></a>설명

영역은 창 내의 원형 또는 다각형 영역입니다. 영역을 사용 하려면 클래스의 멤버로 `CRgn` 정의 된 클리핑 함수를 사용 하 여 클래스의 멤버 함수를 사용 합니다 `CDC` .

멤버 함수는 `CRgn` 호출 되는 지역 개체에 대 한 정보를 만들고, 변경 하 고, 검색 합니다.

사용에 대 한 자세한 내용은 `CRgn` [그래픽 개체](../../mfc/graphic-objects.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="crgncombinergn"></a><a name="combinergn"></a> CRgn:: CombineRgn

두 개의 기존 영역을 결합 하 여 새 GDI 영역을 만듭니다.

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>매개 변수

*pRgn1*<br/>
기존 영역을 식별 합니다.

*pRgn2*<br/>
기존 영역을 식별 합니다.

*nCombineMode*<br/>
두 소스 영역을 결합할 때 수행할 작업을 지정 합니다. 다음 값 중 하나일 수 있습니다.

- RGN_AND는 두 영역 (교차)의 겹치는 영역을 사용 합니다.

- RGN_COPY 지역 1의 복사본을 만듭니다 ( *pRgn1* 으로 식별).

- RGN_DIFF 지역 2 ( *pRgn2* 로 식별 됨)의 일부가 아닌 영역 1 영역 ( *pRgn1* 으로 식별 됨)으로 구성 된 영역을 만듭니다.

- RGN_OR는 두 영역을 전체적으로 결합 합니다 (union).

- RGN_XOR 두 영역을 결합 하지만 겹치는 영역을 제거 합니다.

### <a name="return-value"></a>반환 값

결과 영역의 유형을 지정 합니다. 다음 값 중 하나일 수 있습니다.

- COMPLEXREGION 새 영역에 겹치는 테두리가 있습니다.

- 새로 만든 지역이 없습니다.

- NULLREGION 새 지역이 비어 있습니다.

- SIMPLEREGION 새 지역은 겹치는 테두리를 포함 하지 않습니다.

### <a name="remarks"></a>설명

*NCombineMode* 에 지정 된 대로 지역이 결합 됩니다.

지정 된 두 영역이 결합 되 고 결과 영역 핸들이 개체에 저장 됩니다 `CRgn` . 따라서 개체에 저장 된 모든 지역은 `CRgn` 결합 된 영역으로 대체 됩니다.

지역 크기는 32767 x 32767 논리 단위 또는 64K의 메모리 중 작은 값으로 제한 됩니다.

[CopyRgn](#copyrgn) 를 사용 하 여 한 지역을 다른 지역에 복사 하면 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

## <a name="crgncopyrgn"></a><a name="copyrgn"></a> CRgn:: CopyRgn

*Pr워 src* 에서 정의한 영역을 `CRgn` 개체로 복사 합니다.

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>매개 변수

*pRgnSrc*<br/>
기존 영역을 식별 합니다.

### <a name="return-value"></a>반환 값

결과 영역의 유형을 지정 합니다. 다음 값 중 하나일 수 있습니다.

- COMPLEXREGION 새 영역에 겹치는 테두리가 있습니다.

- 새로 만든 지역이 없습니다.

- NULLREGION 새 지역이 비어 있습니다.

- SIMPLEREGION 새 지역은 겹치는 테두리를 포함 하지 않습니다.

### <a name="remarks"></a>설명

새 지역은 이전에 개체에 저장 된 영역을 대체 합니다 `CRgn` . 이 함수는 [CombineRgn](#combinergn) 멤버 함수의 특수 한 경우입니다.

### <a name="example"></a>예제

  [CRgn:: CreateEllipticRgn](#createellipticrgn)의 예제를 참조 하세요.

## <a name="crgncreateellipticrgn"></a><a name="createellipticrgn"></a> CRgn:: CreateEllipticRgn

원형 영역을 만듭니다.

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
타원 경계 사각형의 왼쪽 위 모퉁이에 대 한 논리 x 좌표를 지정 합니다.

*y1*<br/>
타원 경계 사각형의 왼쪽 위 모퉁이에 대 한 논리 y 좌표를 지정 합니다.

*x2*<br/>
타원의 경계 사각형에 대 한 오른쪽 아래 모퉁이의 논리적 x 좌표를 지정 합니다.

*y2*<br/>
타원의 경계 사각형에 대 한 오른쪽 아래 모퉁이의 논리적 y 좌표를 지정 합니다.

### <a name="return-value"></a>반환 값

작업이 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지역은 *x1*, *y1*, *x2* 및 *y2* 로 지정 된 경계 사각형에 의해 정의 됩니다. 지역은 개체에 저장 됩니다 `CRgn` .

지역 크기는 32767 x 32767 논리 단위 또는 64K의 메모리 중 작은 값으로 제한 됩니다.

함수를 사용 하 여 만든 영역을 사용 하 여 완료 되 면 `CreateEllipticRgn` 응용 프로그램은 장치 컨텍스트에서 영역을 선택 하 고 함수를 사용 하 여 `DeleteObject` 제거 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

## <a name="crgncreateellipticrgnindirect"></a><a name="createellipticrgnindirect"></a> CRgn:: CreateEllipticRgnIndirect

원형 영역을 만듭니다.

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*lpRect*<br/>
`RECT` `CRect` 타원의 경계 사각형 왼쪽 위 모퉁이와 오른쪽 아래 모퉁이의 논리적 좌표를 포함 하는 구조체 또는 개체를 가리킵니다.

### <a name="return-value"></a>반환 값

작업이 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지역은 *lpRect* 가 가리키는 구조 나 개체에 의해 정의 되 고 개체에 저장 됩니다 `CRgn` .

지역 크기는 32767 x 32767 논리 단위 또는 64K의 메모리 중 작은 값으로 제한 됩니다.

함수를 사용 하 여 만든 영역을 사용 하 여 완료 되 면 `CreateEllipticRgnIndirect` 응용 프로그램은 장치 컨텍스트에서 영역을 선택 하 고 함수를 사용 하 여 `DeleteObject` 제거 해야 합니다.

### <a name="example"></a>예제

  [CRgn:: CreateRectRgnIndirect](#createrectrgnindirect)의 예제를 참조 하세요.

## <a name="crgncreatefromdata"></a><a name="createfromdata"></a> CRgn:: CreateFromData

지정 된 영역 및 변환 데이터에서 영역을 만듭니다.

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>매개 변수

*lpXForm*<br/>
는 지역에서 수행할 변환을 정의 하는 [XFORM](/windows/win32/api/wingdi/ns-wingdi-xform)ata 구조를 가리킵니다. 이 포인터가 NULL 이면 id 변환이 사용 됩니다.

*nCount*<br/>
*Pr워 데이터가* 가리키는 바이트 수를 지정 합니다.

*pRgnData*<br/>
지역 데이터를 포함 하는 [R 데이터](/windows/win32/api/wingdi/ns-wingdi-rgndata) 데이터 구조를 가리킵니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

응용 프로그램은 함수를 호출 하 여 지역에 대 한 데이터를 검색할 수 있습니다 `CRgn::GetRegionData` .

## <a name="crgncreatefrompath"></a><a name="createfrompath"></a> CRgn:: CreateFromPath

지정 된 장치 컨텍스트에 선택한 경로에서 영역을 만듭니다.

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
닫힌 경로를 포함 하는 장치 컨텍스트를 식별 합니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*PDC* 매개 변수로 식별 되는 장치 컨텍스트에는 닫힌 경로가 포함 되어야 합니다. `CreateFromPath`에서 경로를 영역으로 변환 하면 Windows에서 장치 컨텍스트에서 닫힌 경로를 삭제 합니다.

## <a name="crgncreatepolygonrgn"></a><a name="createpolygonrgn"></a> CRgn:: CreatePolygonRgn

다각형 영역을 만듭니다.

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>매개 변수

*lpPoints*<br/>
구조체의 배열 `POINT` 또는 개체의 배열을 가리킵니다 `CPoint` . 각 구조체는 다각형의 한 꼭 짓 점에 대 한 x 좌표와 y 좌표를 지정 합니다. `POINT`구조체의 형식은 다음과 같습니다.

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
`POINT` `CPoint` *Lppoints* 가 가리키는 배열의 구조체 또는 개체 수를 지정 합니다.

*nMode*<br/>
영역에 대 한 채우기 모드를 지정 합니다. 이 매개 변수는 대체 또는 굴곡 중 하나일 수 있습니다.

### <a name="return-value"></a>반환 값

작업이 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

필요한 경우 마지막 정점부터 첫 번째 정점까지 선을 그려 시스템에서 다각형이 자동으로 닫힙니다. 결과 영역은 개체에 저장 됩니다 `CRgn` .

지역 크기는 32767 x 32767 논리 단위 또는 64K의 메모리 중 작은 값으로 제한 됩니다.

다각형 채우기 모드가 대체 인 경우 시스템은 각 검사 줄에서 홀수 번호와 짝수 번호의 다각형 면으로 영역을 채웁니다. 즉, 시스템에서 첫 번째와 두 번째 쪽 사이, 세 번째와 네 번째 쪽 사이의 영역을 채웁니다.

다각형 채우기 모드가 굴곡 인 경우 시스템은 그림을 그린 방향을 사용 하 여 영역을 채울 것인지 여부를 결정 합니다. 다각형의 각 선 세그먼트는 시계 방향 또는 반시계 방향으로 그려집니다. 바깥쪽 영역에서 그림 바깥쪽으로 그린 허수 줄이 시계 방향 선 세그먼트를 통과 하면 개수가 증가 합니다. 선이 반시계 방향 선 세그먼트를 통과 하면 개수가 감소 합니다. 줄이 그림의 외부에 도달 하면 개수가 0이 아닌 경우 영역이 채워집니다.

응용 프로그램은 함수를 사용 하 여 만든 영역을 사용 하 여 완료 된 경우 `CreatePolygonRgn` 장치 컨텍스트에서 지역을 선택 하 고 함수를 사용 하 여 `DeleteObject` 제거 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

## <a name="crgncreatepolypolygonrgn"></a><a name="createpolypolygonrgn"></a> CRgn:: CreatePolyPolygonRgn

일련의 폐쇄형 다각형으로 구성 된 영역을 만듭니다.

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>매개 변수

*lpPoints*<br/>
`POINT` `CPoint` 다각형의 꼭 짓 점을 정의 하는 구조체의 배열 또는 개체의 배열을 가리킵니다. 각 다각형은 시스템에서 자동으로 닫히지 않으므로 명시적으로 닫아야 합니다. 다각형이 연속적으로 지정 됩니다. `POINT`구조체의 형식은 다음과 같습니다.

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
는 정수 배열을 가리킵니다. 첫 번째 정수는 *Lppoints* 배열의 첫 번째 다각형에 있는 꼭 짓 점의 수를 지정 하 고 두 번째 정수는 두 번째 다각형의 꼭 짓 점 수를 지정 합니다.

*nCount*<br/>
*LpPolyCounts* 배열의 전체 정수 수를 지정 합니다.

*nPolyFillMode*<br/>
다각형 채우기 모드를 지정 합니다. 이 값은 대체 또는 굴곡 중 하나일 수 있습니다.

### <a name="return-value"></a>반환 값

작업이 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

결과 영역은 개체에 저장 됩니다 `CRgn` .

다각형이 분리 되어 있거나 겹칠 수 있습니다.

지역 크기는 32767 x 32767 논리 단위 또는 64K의 메모리 중 작은 값으로 제한 됩니다.

다각형 채우기 모드가 대체 인 경우 시스템은 각 검사 줄에서 홀수 번호와 짝수 번호의 다각형 면으로 영역을 채웁니다. 즉, 시스템에서 첫 번째와 두 번째 쪽 사이, 세 번째와 네 번째 쪽 사이의 영역을 채웁니다.

다각형 채우기 모드가 굴곡 인 경우 시스템은 그림을 그린 방향을 사용 하 여 영역을 채울 것인지 여부를 결정 합니다. 다각형의 각 선 세그먼트는 시계 방향 또는 반시계 방향으로 그려집니다. 바깥쪽 영역에서 그림 바깥쪽으로 그린 허수 줄이 시계 방향 선 세그먼트를 통과 하면 개수가 증가 합니다. 선이 반시계 방향 선 세그먼트를 통과 하면 개수가 감소 합니다. 줄이 그림의 외부에 도달 하면 개수가 0이 아닌 경우 영역이 채워집니다.

응용 프로그램이 함수를 사용 하 여 만든 영역을 사용 하 여 완료 되 면 `CreatePolyPolygonRgn` 장치 컨텍스트에서 지역을 선택 하 고 [CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) 멤버 함수를 사용 하 여 제거 해야 합니다.

## <a name="crgncreaterectrgn"></a><a name="createrectrgn"></a> CRgn:: CreateRectRgn

개체에 저장 되는 사각형 영역을 만듭니다 `CRgn` .

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
영역의 왼쪽 위 모퉁이에 대 한 논리 x 좌표를 지정 합니다.

*y1*<br/>
영역의 왼쪽 위 모퉁이에 대 한 논리 y 좌표를 지정 합니다.

*x2*<br/>
영역의 오른쪽 아래 모퉁이에 대 한 논리 x 좌표를 지정 합니다.

*y2*<br/>
영역의 오른쪽 아래 모퉁이에 대 한 논리 y 좌표를 지정 합니다.

### <a name="return-value"></a>반환 값

작업이 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지역 크기는 32767 x 32767 논리 단위 또는 64K의 메모리 중 작은 값으로 제한 됩니다.

에서 만든 영역을 사용 하 여 완료 되 면 `CreateRectRgn` 응용 프로그램은 [CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) 멤버 함수를 사용 하 여 영역을 제거 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

추가 예제는 [CRgn:: CombineRgn](#combinergn)를 참조 하세요.

## <a name="crgncreaterectrgnindirect"></a><a name="createrectrgnindirect"></a> CRgn:: CreateRectRgnIndirect

개체에 저장 되는 사각형 영역을 만듭니다 `CRgn` .

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*lpRect*<br/>
`RECT` `CRect` 영역의 왼쪽 위 모퉁이와 오른쪽 아래 모퉁이의 논리적 좌표를 포함 하는 구조체 또는 개체를 가리킵니다. `RECT`구조체의 형식은 다음과 같습니다.

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>반환 값

작업이 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지역 크기는 32767 x 32767 논리 단위 또는 64K의 메모리 중 작은 값으로 제한 됩니다.

에서 만든 영역을 사용 하 여 완료 되 면 `CreateRectRgnIndirect` 응용 프로그램은 [CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) 멤버 함수를 사용 하 여 영역을 제거 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

## <a name="crgncreateroundrectrgn"></a><a name="createroundrectrgn"></a> CRgn:: CreateRoundRectRgn

개체에 저장 된 모퉁이가 둥근 사각형 영역을 만듭니다 `CRgn` .

```
BOOL CreateRoundRectRgn(
    int x1,
    int y1,
    int x2,
    int y2,
    int x3,
    int y3);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
영역의 왼쪽 위 모퉁이에 대 한 논리 x 좌표를 지정 합니다.

*y1*<br/>
영역의 왼쪽 위 모퉁이에 대 한 논리 y 좌표를 지정 합니다.

*x2*<br/>
영역의 오른쪽 아래 모퉁이에 대 한 논리 x 좌표를 지정 합니다.

*y2*<br/>
영역의 오른쪽 아래 모퉁이에 대 한 논리 y 좌표를 지정 합니다.

*x3*<br/>
모퉁이가 둥근 모퉁이를 만드는 데 사용 되는 타원의 너비를 지정 합니다.

*y3*<br/>
모퉁이가 둥근 모퉁이를 만드는 데 사용 되는 타원의 높이를 지정 합니다.

### <a name="return-value"></a>반환 값

작업이 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지역 크기는 32767 x 32767 논리 단위 또는 64K의 메모리 중 작은 값으로 제한 됩니다.

응용 프로그램이 함수를 사용 하 여 만든 영역을 사용 하 여 완료 되 면 `CreateRoundRectRgn` 장치 컨텍스트에서 지역을 선택 하 고 [CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) 멤버 함수를 사용 하 여 제거 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

## <a name="crgncrgn"></a><a name="crgn"></a> CRgn:: CRgn

`CRgn` 개체를 생성합니다.

```
CRgn();
```

### <a name="remarks"></a>설명

`m_hObject`하나 이상의 다른 멤버 함수를 사용 하 여 개체를 초기화할 때까지 데이터 멤버에 올바른 WINDOWS GDI 지역이 포함 되지 않습니다 `CRgn` .

### <a name="example"></a>예제

  [CRgn:: CreateRoundRectRgn](#createroundrectrgn)의 예제를 참조 하세요.

## <a name="crgnequalrgn"></a><a name="equalrgn"></a> CRgn:: EqualRgn

지정 된 지역이 개체에 저장 된 영역과 동일한 지 여부를 확인 합니다 `CRgn` .

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>매개 변수

*pRgn*<br/>
영역을 식별 합니다.

### <a name="return-value"></a>반환 값

두 지역이 동일한 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

## <a name="crgnfromhandle"></a><a name="fromhandle"></a> CRgn:: FromHandle

`CRgn`Windows 영역에 대 한 핸들을 지정 하면 개체에 대 한 포인터를 반환 합니다.

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>매개 변수

*hRgn*<br/>
Windows 영역에 대 한 핸들을 지정 합니다.

### <a name="return-value"></a>반환 값

`CRgn` 개체에 대한 포인터입니다. 함수가 실패 하면 반환 값은 NULL입니다.

### <a name="remarks"></a>설명

`CRgn`개체가 핸들에 아직 연결 되지 않은 경우 임시 `CRgn` 개체가 생성 되 고 연결 됩니다. 이 임시 `CRgn` 개체는 다음에 응용 프로그램이 이벤트 루프에서 유휴 시간을 초과 하 여 모든 임시 그래픽 개체가 삭제 될 때 까지만 유효 합니다. 이에 대 한 또 다른 방법은 임시 개체가 하나의 창 메시지를 처리 하는 동안에만 유효 하다는 것입니다.

## <a name="crgngetregiondata"></a><a name="getregiondata"></a> CRgn:: Get지역 데이터

지정 된 버퍼를 영역을 설명 하는 데이터로 채웁니다.

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>매개 변수

*lpRgnData*<br/>
정보를 받는 [R 데이터](/windows/win32/api/wingdi/ns-wingdi-rgndata) 데이터 구조를 가리킵니다. 이 매개 변수가 NULL 이면 반환 값에는 지역 데이터에 필요한 바이트 수가 포함 됩니다.

*nCount*<br/>
*Lpr워 데이터* 버퍼의 크기 (바이트)를 지정 합니다.

### <a name="return-value"></a>반환 값

함수가 성공 하 고 *Ncount* 에서 적절 한 바이트 수를 지정 하는 경우 반환 값은 항상 *ncount* 입니다. 함수가 실패 하거나 *Ncount* 에서 적절 한 바이트 수를 지정 하는 경우 반환 값은 0 (오류)입니다.

### <a name="remarks"></a>설명

이 데이터는 영역을 구성 하는 사각형의 크기를 포함 합니다. 이 함수는 함수와 함께 사용 됩니다 `CRgn::CreateFromData` .

## <a name="crgngetrgnbox"></a><a name="getrgnbox"></a> CRgn:: GetRgnBox

개체의 경계 사각형의 좌표를 검색 `CRgn` 합니다.

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>매개 변수

*lpRect*<br/>
`RECT` `CRect` 경계 사각형의 좌표를 받는 구조체 또는 개체를 가리킵니다. `RECT`구조체의 형식은 다음과 같습니다.

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>반환 값

영역의 유형을 지정 합니다. 다음 값 중 하나일 수 있습니다.

- COMPLEXREGION 영역에 겹치는 테두리가 있습니다.

- NULLREGION 지역이 비어 있습니다.

- 오류 `CRgn` 개체에서 유효한 영역을 지정 하지 않습니다.

- SIMPLEREGION 영역에 겹치는 테두리가 없습니다.

### <a name="example"></a>예제

  [CRgn:: CreatePolygonRgn](#createpolygonrgn)의 예제를 참조 하세요.

## <a name="crgnoffsetrgn"></a><a name="offsetrgn"></a> CRgn:: OffsetRgn

개체에 저장 된 영역을 `CRgn` 지정 된 오프셋으로 이동 합니다.

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
왼쪽 또는 오른쪽으로 이동할 단위 수를 지정 합니다.

*y*<br/>
위나 아래로 이동할 단위 수를 지정 합니다.

*까지*<br/>
*점의* x 좌표는 왼쪽 또는 오른쪽으로 이동할 단위 수를 지정 합니다. *점의* y 좌표는 위나 아래로 이동할 단위 수를 지정 합니다. *Point* 매개 변수는 `POINT` 구조체 또는 개체 중 하나일 수 있습니다 `CPoint` .

### <a name="return-value"></a>반환 값

새 지역의 형식입니다. 다음 값 중 하나일 수 있습니다.

- COMPLEXREGION 영역에 겹치는 테두리가 있습니다.

- 오류 영역 핸들이 잘못 되었습니다.

- NULLREGION 지역이 비어 있습니다.

- SIMPLEREGION 영역에 겹치는 테두리가 없습니다.

### <a name="remarks"></a>설명

함수는 y 축을 따라 x 축과 *y* 단위를 따라 지역 *x* 단위를 이동 합니다.

영역의 좌표 값은 32767 보다 작거나 같고-32768 보다 크거나 같아야 합니다. 잘못 된 영역 좌표를 방지 하려면 *x* 및 *y* 매개 변수를 신중 하 게 선택 해야 합니다.

### <a name="example"></a>예제

  [CRgn:: CreateEllipticRgn](#createellipticrgn)의 예제를 참조 하세요.

## <a name="crgnoperator-hrgn"></a><a name="operator_hrgn"></a> CRgn:: operator HRGN

이 연산자를 사용 하 여 개체의 연결 된 Windows GDI 핸들을 가져옵니다 `CRgn` .

```
operator HRGN() const;
```

### <a name="return-value"></a>반환 값

성공 하면 개체가 나타내는 Windows GDI 개체에 대 한 핸들이 고, `CRgn` 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 연산자는 HRGN 개체의 직접 사용을 지 원하는 캐스팅 연산자입니다.

그래픽 개체를 사용 하는 방법에 대 한 자세한 내용은 Windows SDK의 [그래픽 개체](/windows/win32/gdi/graphic-objects) 문서를 참조 하세요.

## <a name="crgnptinregion"></a><a name="ptinregion"></a> CRgn::P tInRegion

*X* 및 *y* 로 지정 된 점이 개체에 저장 된 영역에 있는지 여부를 확인 `CRgn` 합니다.

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>매개 변수

*x*<br/>
테스트할 지점의 논리 x 좌표를 지정 합니다.

*y*<br/>
테스트할 점의 논리 y 좌표를 지정 합니다.

*까지*<br/>
*점의* x 및 y 좌표는 값을 테스트할 점의 x 및 y 좌표를 지정 합니다. *Point* 매개 변수는 `POINT` 구조체 또는 개체 중 하나일 수 있습니다 `CPoint` .

### <a name="return-value"></a>반환 값

지점이 영역에 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="crgnrectinregion"></a><a name="rectinregion"></a> CRgn:: RectInRegion

*LpRect* 에 의해 지정 된 사각형의 일부가 개체에 저장 된 영역의 경계 내에 있는지 여부를 확인 합니다 `CRgn` .

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>매개 변수

*lpRect*<br/>
는 `RECT` 구조체 또는 개체를 가리킵니다 `CRect` . `RECT`구조체의 형식은 다음과 같습니다.

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>반환 값

지정 된 사각형의 일부가 영역의 경계 내에 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="crgnsetrectrgn"></a><a name="setrectrgn"></a> CRgn:: SetRectRgn

사각형 영역을 만듭니다.

```cpp
void SetRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);

void SetRectRgn(LPCRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
사각형 영역의 왼쪽 위 모퉁이에 대 한 x 좌표를 지정 합니다.

*y1*<br/>
사각형 영역의 왼쪽 위 모퉁이에 대 한 y 좌표를 지정 합니다.

*x2*<br/>
사각형 영역의 오른쪽 아래 모퉁이의 x 좌표를 지정 합니다.

*y2*<br/>
사각형 영역의 오른쪽 아래 모퉁이의 y 좌표를 지정 합니다.

*lpRect*<br/>
사각형 영역을 지정 합니다. 는 구조체에 대 한 포인터 이거나 개체 일 수 있습니다 `RECT` `CRect` .

### <a name="remarks"></a>설명

그러나 [CreateRectRgn](#createrectrgn)와 달리 로컬 Windows 응용 프로그램 힙에서는 추가 메모리를 할당 하지 않습니다. 대신 개체에 저장 된 영역에 할당 된 공간을 사용 합니다 `CRgn` . 즉,을 `CRgn` 호출 하기 전에 개체가 유효한 Windows 영역으로 이미 초기화 된 상태 여야 합니다 `SetRectRgn` . *X1*, *y1*, *x2* 및 *y2* 로 제공 되는 점은 할당 된 공간의 최소 크기를 지정 합니다.

`CreateRectRgn`로컬 메모리 관리자에 대 한 호출을 방지 하려면 멤버 함수 대신이 함수를 사용 합니다.

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
