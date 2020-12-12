---
description: '자세한 정보: CPoint 클래스'
title: CPoint 클래스
ms.date: 11/04/2016
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
ms.openlocfilehash: 9d1c6ecb628e4d47d80503bb7a441efc4deb1252
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166761"
---
# <a name="cpoint-class"></a>CPoint 클래스

Windows `POINT` 구조체와 유사합니다.

## <a name="syntax"></a>구문

```
class CPoint : public tagPOINT
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CPoint:: CPoint](#cpoint)|`CPoint`를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPoint:: Offset](#offset)|의 및 멤버에 값을 추가 `x` `y` `CPoint` 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CPoint:: operator-](#operator_-)|및 크기의 차, `CPoint` 점의 부정 또는 두 점 사이의 크기 차이 또는 음수 크기의 오프셋을 반환 합니다.|
|[CPoint:: operator! =](#operator_neq)|두 점이 같지 않은지 확인 합니다.|
|[CPoint:: operator +](#operator_add)|`CPoint`및 크기 또는 점의 합계와 크기를 기준으로 하는 오프셋을 반환 합니다 `CRect` .|
|[CPoint:: operator + =](#operator_add_eq)|`CPoint`크기 또는 점을 추가 하 여 오프셋 합니다.|
|[CPoint:: operator-=](#operator_-_eq)|`CPoint`크기 또는 점을 빼서 오프셋 합니다.|
|[CPoint:: operator = =](#operator_eq_eq)|두 점이 일치 하는지 확인 합니다.|

## <a name="remarks"></a>설명

또한 `CPoint` 및 [요소](/windows/win32/api/windef/ns-windef-point) 구조를 조작 하는 멤버 함수도 포함 됩니다.

`CPoint`구조체를 사용 하는 모든 위치에서 개체를 사용할 수 있습니다 `POINT` . "Size"와 상호 작용 하는이 클래스의 연산자는 [Csize](../../atl-mfc-shared/reference/csize-class.md) 개체 또는 [크기](/windows/win32/api/windef/ns-windef-size) 구조를 사용할 수 있습니다. 두 가지는 서로 교환이 가능 합니다.

> [!NOTE]
> 이 클래스는 구조체에서 파생 됩니다 `tagPOINT` . (이름은 `tagPOINT` 일반적으로 사용 되지 않는 구조체 이름입니다 `POINT` .) 즉, 및 구조체의 데이터 멤버는 `POINT` `x` `y` 의 데이터 멤버에 액세스할 수 있습니다 `CPoint` .

> [!NOTE]
> 공유 유틸리티 클래스 (예:)에 대 한 자세한 내용은 `CPoint` [공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`tagPOINT`

`CPoint`

## <a name="requirements"></a>요구 사항

**헤더:** 이 형식 .h

## <a name="cpointcpoint"></a><a name="cpoint"></a> CPoint:: CPoint

`CPoint` 개체를 생성합니다.

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### <a name="parameters"></a>매개 변수

*initX*<br/>
`x`의 `CPoint` 멤버 값을 지정합니다.

*initY*<br/>
`y`의 `CPoint` 멤버 값을 지정합니다.

*initPt*<br/>
[요소](/windows/win32/api/windef/ns-windef-point) 구조 또는를 `CPoint` 초기화 하는 데 사용 되는 값을 지정 하는입니다 `CPoint` .

*initSize*<br/>
초기화에 사용 되는 값을 지정 하는 [크기](/windows/win32/api/windef/ns-windef-size) 구조 또는 [csize](../../atl-mfc-shared/reference/csize-class.md) 입니다 `CPoint` .

*dwPoint*<br/>
멤버를 `x` *dwpoint* 의 하위 단어로 설정 하 고 `y` 멤버를 *dwpoint* 의 상위 단어로 설정 합니다.

### <a name="remarks"></a>설명

인수가 지정되지 않으면 `x` 및 `y` 멤버가 0으로 설정됩니다.

### <a name="example"></a>예제

```cpp
CPoint   ptTopLeft(0, 0);
// works from a POINT, too

POINT   ptHere;
ptHere.x = 35;
ptHere.y = 95;

CPoint   ptMFCHere(ptHere);

// works from a SIZE
SIZE   sHowBig;
sHowBig.cx = 300;
sHowBig.cy = 10;

CPoint ptMFCBig(sHowBig);
// or from a DWORD

DWORD   dwSize;
dwSize = MAKELONG(35, 95);

CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```

## <a name="cpointoffset"></a><a name="offset"></a> CPoint:: Offset

의 및 멤버에 값을 추가 `x` `y` `CPoint` 합니다.

```cpp
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>매개 변수

*xOffset*<br/>
의 멤버를 오프셋할 크기를 지정 합니다 `x` `CPoint` .

*yOffset*<br/>
의 멤버를 오프셋할 크기를 지정 합니다 `y` `CPoint` .

*까지*<br/>
을 오프셋할 크기 ( [포인트](/windows/win32/api/windef/ns-windef-point) 또는 `CPoint` )를 지정 합니다 `CPoint` .

*size*<br/>
을 오프셋할 크기 ( [크기](/windows/win32/api/windef/ns-windef-size) 또는 [csize](../../atl-mfc-shared/reference/csize-class.md))를 지정 합니다 `CPoint` .

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

## <a name="cpointoperator-"></a><a name="operator_eq_eq"></a> CPoint:: operator = =

두 점이 일치 하는지 확인 합니다.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
[점](/windows/win32/api/windef/ns-windef-point) 구조 또는 개체를 포함 `CPoint` 합니다.

### <a name="return-value"></a>반환 값

점이 같으면 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

## <a name="cpointoperator-"></a><a name="operator_neq"></a> CPoint:: operator! =

두 점이 같지 않은지 확인 합니다.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
[점](/windows/win32/api/windef/ns-windef-point) 구조 또는 개체를 포함 `CPoint` 합니다.

### <a name="return-value"></a>반환 값

점이 같지 않으면 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add_eq"></a> CPoint:: operator + =

첫 번째 오버 로드는에 크기를 추가 합니다 `CPoint` .

```cpp
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>매개 변수

*size*<br/>
에는 [크기](/windows/win32/api/windef/ns-windef-size) 구조 또는 [csize](../../atl-mfc-shared/reference/csize-class.md) 개체가 포함 되어 있습니다.

*까지*<br/>
[점](/windows/win32/api/windef/ns-windef-point) 구조 또는 [cpoint](../../atl-mfc-shared/reference/cpoint-class.md) 개체를 포함 합니다.

### <a name="remarks"></a>설명

두 번째 오버 로드는에 점을 추가 합니다 `CPoint` .

두 경우 모두 `x` 오른쪽 피연산자의 (또는) 멤버를의 멤버에 추가 하 `cx` `x` `CPoint` 고 `y` 오른쪽 피연산자의 (또는) 멤버를의 `cy` 멤버에 추가 `y` `CPoint` 하 여 추가 작업을 수행 합니다.

예를 들어를 포함 하는 변수에를 추가 하면 `CPoint(5, -7)` `CPoint(30, 40)` 변수가로 변경 `CPoint(35, 33)` 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-_eq"></a> CPoint:: operator-=

첫 번째 오버 로드는에서 크기를 뺍니다 `CPoint` .

```cpp
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>매개 변수

*size*<br/>
에는 [크기](/windows/win32/api/windef/ns-windef-size) 구조 또는 [csize](../../atl-mfc-shared/reference/csize-class.md) 개체가 포함 되어 있습니다.

*까지*<br/>
[점](/windows/win32/api/windef/ns-windef-point) 구조 또는 [cpoint](../../atl-mfc-shared/reference/cpoint-class.md) 개체를 포함 합니다.

### <a name="remarks"></a>설명

두 번째 오버 로드는에서 점을 뺍니다 `CPoint` .

두 경우 모두 빼기는의 `x` `cx` 멤버에서 오른쪽 피연산자의 (또는) 멤버를 빼서 `x` `CPoint` `y` `cy` 의 멤버에서 오른쪽 피연산자의 (또는) 멤버를 빼서 수행 `y` `CPoint` 합니다.

예를 들어를 `CPoint(5, -7)` 포함 하는 변수에서 빼서 `CPoint(30, 40)` 변수를로 변경 `CPoint(25, 47)` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add"></a> CPoint:: operator +

이 연산자를 사용 하 여 또는 개체로 오프셋 하거나를 사용 하 여를 `CPoint` `CPoint` `CSize` 오프셋 `CRect` `CPoint` 합니다.

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>매개 변수

*size*<br/>
에는 [크기](/windows/win32/api/windef/ns-windef-size) 구조 또는 [csize](../../atl-mfc-shared/reference/csize-class.md) 개체가 포함 되어 있습니다.

*까지*<br/>
[점](/windows/win32/api/windef/ns-windef-point) 구조 또는 [cpoint](../../atl-mfc-shared/reference/cpoint-class.md) 개체를 포함 합니다.

*lpRect*<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect) 구조 또는 [crect](../../atl-mfc-shared/reference/crect-class.md) 개체에 대 한 포인터를 포함 합니다.

### <a name="return-value"></a>반환 값

`CPoint`크기, `CPoint` 점으로 오프셋 되는 또는 점으로 오프셋 되는입니다 `CRect` .

### <a name="remarks"></a>설명

예를 들어 처음 두 오버 로드 중 하나를 사용 하 여 점 `CPoint(25, -19)` 또는 크기로 점을 오프셋 하면 `CPoint(15, 5)` 값이 `CSize(15, 5)` 반환 `CPoint(40, -14)` 됩니다.

점에 사각형을 추가 하면 점에 지정 된 및 값에 의해 오프셋 된 후에 사각형이 반환 `x` `y` 됩니다. 예를 들어 마지막 오버 로드를 사용 하 여 점으로 사각형을 오프셋 하면이 `CRect(125, 219, 325, 419)` `CPoint(25, -19)` 반환 `CRect(150, 200, 350, 400)` 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-"></a> CPoint:: operator-

처음 두 오버 로드 중 하나를 사용 하 여 `CPoint` 또는 `CSize` 개체를 뺍니다 `CPoint` .

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
[점](/windows/win32/api/windef/ns-windef-point) 구조 또는 [cpoint](../../atl-mfc-shared/reference/cpoint-class.md) 개체입니다.

*size*<br/>
[크기](/windows/win32/api/windef/ns-windef-size) 구조체 또는 [csize](../../atl-mfc-shared/reference/csize-class.md) 개체입니다.

*lpRect*<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect) 구조 또는 [crect](../../atl-mfc-shared/reference/crect-class.md) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

`CSize`두 점, 크기의 부정을 기준으로 하는, 점의 부정으로 오프셋 되는, `CPoint` `CRect` `CPoint` 점의 부정 인입니다 (점)의 차이를 나타내는입니다.

### <a name="remarks"></a>설명

세 번째 오버 로드는 `CRect` 의 부정을를 오프셋 합니다 `CPoint` . 마지막으로 단항 연산자를 사용 하 여 부정 `CPoint` 합니다.

예를 들어 첫 번째 오버 로드를 사용 하 여 두 점의 차이를 찾고을 `CPoint(25, -19)` `CPoint(15, 5)` 반환 `CSize(10, -24)` 합니다.

에서를 `CSize` 빼면 `CPoint` 위와 동일한 계산을 수행 하지만 `CPoint` 개체가 아닌 개체를 반환 합니다 `CSize` . 예를 들어 두 번째 오버 로드를 사용 하 여 지점과 크기 사이의 차이를 찾으려면를 `CPoint(25, -19)` `CSize(15, 5)` 반환 `CPoint(10, -24)` 합니다.

점에서 사각형을 빼면 점에 지정 된 및 값의 네거티브에 의해 사각형 오프셋이 `x` 반환 `y` 됩니다. 예를 들어 마지막 오버 로드를 사용 하 여 점에 의해 사각형을 오프셋 하면이 `CRect(125, 200, 325, 400)` `CPoint(25, -19)` 반환 `CRect(100, 219, 300, 419)` 됩니다.

단항 연산자를 사용 하 여 점을 부정할 수 있습니다. 예를 들어 점에서 단항 연산자를 사용 하면이 `CPoint(25, -19)` 반환 `CPoint(-25, 19)` 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 MDI](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[POINT 구조체](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect 클래스](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize 클래스](../../atl-mfc-shared/reference/csize-class.md)
