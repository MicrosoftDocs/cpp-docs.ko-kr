---
description: '자세히 알아보기: CD2DGeometrySink 클래스'
title: CD2DGeometrySink 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::AddArc
- AFXRENDERTARGET/CD2DGeometrySink::AddBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddBeziers
- AFXRENDERTARGET/CD2DGeometrySink::AddLine
- AFXRENDERTARGET/CD2DGeometrySink::AddLines
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBeziers
- AFXRENDERTARGET/CD2DGeometrySink::BeginFigure
- AFXRENDERTARGET/CD2DGeometrySink::Close
- AFXRENDERTARGET/CD2DGeometrySink::EndFigure
- AFXRENDERTARGET/CD2DGeometrySink::Get
- AFXRENDERTARGET/CD2DGeometrySink::IsValid
- AFXRENDERTARGET/CD2DGeometrySink::SetFillMode
- AFXRENDERTARGET/CD2DGeometrySink::SetSegmentFlags
- AFXRENDERTARGET/CD2DGeometrySink::m_pSink
helpviewer_keywords:
- CD2DGeometrySink [MFC], CD2DGeometrySink
- CD2DGeometrySink [MFC], AddArc
- CD2DGeometrySink [MFC], AddBezier
- CD2DGeometrySink [MFC], AddBeziers
- CD2DGeometrySink [MFC], AddLine
- CD2DGeometrySink [MFC], AddLines
- CD2DGeometrySink [MFC], AddQuadraticBezier
- CD2DGeometrySink [MFC], AddQuadraticBeziers
- CD2DGeometrySink [MFC], BeginFigure
- CD2DGeometrySink [MFC], Close
- CD2DGeometrySink [MFC], EndFigure
- CD2DGeometrySink [MFC], Get
- CD2DGeometrySink [MFC], IsValid
- CD2DGeometrySink [MFC], SetFillMode
- CD2DGeometrySink [MFC], SetSegmentFlags
- CD2DGeometrySink [MFC], m_pSink
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
ms.openlocfilehash: e7916cdb39272e924a9d6ef6c0a8322d8ce6fb1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193424"
---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink 클래스

ID2D1GeometrySink에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DGeometrySink;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DGeometrySink:: CD2DGeometrySink](#cd2dgeometrysink)|CD2DPathGeometry 개체에서 CD2DGeometrySink 개체를 생성 합니다.|
|[CD2DGeometrySink:: ~ CD2DGeometrySink](#_dtorcd2dgeometrysink)|소멸자입니다. D2D geometry 싱크 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DGeometrySink:: AddArc](#addarc)|경로 기 하 도형에 단일 호를 추가 합니다.|
|[CD2DGeometrySink:: AddBezier 지 어](#addbezier)|현재 점과 지정된 끝점 간에 입방형 3차원 곡선을 만듭니다.|
|[CD2DGeometrySink:: AddBeziers](#addbeziers)|입방 형 3 차원 곡선의 시퀀스를 만들고 기 하 도형 싱크에 추가 합니다.|
|[CD2DGeometrySink:: AddLine](#addline)|현재 지점과 지정 된 끝점 사이에 선 세그먼트를 만들어 기 하 도형 싱크에 추가 합니다.|
|[CD2DGeometrySink:: AddLines](#addlines)|지정 된 요소를 사용 하 여 선 시퀀스를 만들고 기 하 도형 싱크에 추가 합니다.|
|[CD2DGeometrySink:: AddQuadraticBezier](#addquadraticbezier)|현재 점과 지정된 끝점 간에 정방형 3차원 곡선을 만듭니다.|
|[CD2DGeometrySink:: AddQuadraticBeziers](#addquadraticbeziers)|단일 호출에서 정방형 3 차원 세그먼트의 시퀀스를 배열로 추가 합니다.|
|[CD2DGeometrySink:: BeginFigure](#beginfigure)|지정 된 지점에서 새 그림을 시작 합니다.|
|[CD2DGeometrySink:: Close](#close)|기 하 도형 싱크를 닫습니다.|
|[CD2DGeometrySink:: EndFigure](#endfigure)|현재 그림을 종료 합니다. 필요에 따라 닫습니다.|
|[CD2DGeometrySink:: Get](#get)|ID2D1GeometrySink 인터페이스를 반환 합니다.|
|[CD2DGeometrySink:: IsValid](#isvalid)|기 하 도형 싱크 유효성 검사|
|[CD2DGeometrySink:: SetFillMode](#setfillmode)|이 기 하 도형 싱크에 의해 설명 되는 기 하 도형 내에 있는 점과 외부의 위치를 결정 하는 데 사용 되는 메서드를 지정 합니다.|
|[CD2DGeometrySink:: SetSegmentFlags](#setsegmentflags)|기 하 도형 싱크에 추가 된 새 세그먼트에 적용할 스트로크 및 조인 옵션을 지정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DGeometrySink:: operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|ID2D1GeometrySink 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CD2DGeometrySink:: m_pSink](#m_psink)|ID2D1GeometrySink에 대 한 포인터입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CD2DGeometrySink`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="_dtorcd2dgeometrysink"></a> CD2DGeometrySink:: ~ CD2DGeometrySink

소멸자입니다. D2D geometry 싱크 개체가 제거 될 때 호출 됩니다.

```
virtual ~CD2DGeometrySink();
```

## <a name="cd2dgeometrysinkaddarc"></a><a name="addarc"></a> CD2DGeometrySink:: AddArc

경로 기 하 도형에 단일 호를 추가 합니다.

```cpp
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>매개 변수

*원호의*<br/>
그림에 추가할 호 세그먼트입니다.

## <a name="cd2dgeometrysinkaddbezier"></a><a name="addbezier"></a> CD2DGeometrySink:: AddBezier 지 어

현재 점과 지정된 끝점 간에 입방형 3차원 곡선을 만듭니다.

```cpp
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>매개 변수

*3*<br/>
추가할 베 지 어 곡선의 제어점과 끝점을 설명 하는 구조체입니다.

## <a name="cd2dgeometrysinkaddbeziers"></a><a name="addbeziers"></a> CD2DGeometrySink:: AddBeziers

입방 형 3 차원 곡선의 시퀀스를 만들고 기 하 도형 싱크에 추가 합니다.

```cpp
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>매개 변수

*beziers*<br/>
만들 베 지 어 곡선을 설명 하는 베 지 어 세그먼트의 배열입니다. 기 하 도형 싱크 현재 지점 (그려진 마지막 세그먼트의 끝점 또는 BeginFigure에서 지정한 위치)에서 배열에 있는 첫 번째 베 지 어 세그먼트의 끝점으로 곡선이 그려집니다. 배열에 추가 3 차원 세그먼트가 포함 된 경우 각 후속 베 지 어 세그먼트는 이전 베 지 어 세그먼트의 끝점을 시작 지점으로 사용 합니다.

## <a name="cd2dgeometrysinkaddline"></a><a name="addline"></a> CD2DGeometrySink:: AddLine

현재 지점과 지정 된 끝점 사이에 선 세그먼트를 만들어 기 하 도형 싱크에 추가 합니다.

```cpp
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
그릴 선의 끝점입니다.

## <a name="cd2dgeometrysinkaddlines"></a><a name="addlines"></a> CD2DGeometrySink:: AddLines

지정 된 요소를 사용 하 여 선 시퀀스를 만들고 기 하 도형 싱크에 추가 합니다.

```cpp
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>매개 변수

*확장점*<br/>
그릴 선을 설명 하는 하나 이상의 점으로 이루어진 배열입니다. 기 하 도형 싱크의 현재 지점 (그려진 마지막 세그먼트의 끝점 또는 BeginFigure에서 지정한 위치)에서 배열의 첫 번째 점으로 선을 그립니다. 배열에 추가 점이 포함 된 경우 첫 번째 점에서 배열의 두 번째 점, 두 번째 점에서 세 번째 지점까지 선이 그려집니다. 그릴 선의 끝점 시퀀스의 배열입니다.

## <a name="cd2dgeometrysinkaddquadraticbezier"></a><a name="addquadraticbezier"></a> CD2DGeometrySink:: AddQuadraticBezier

현재 점과 지정된 끝점 간에 정방형 3차원 곡선을 만듭니다.

```cpp
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>매개 변수

*3*<br/>
추가할 정방형 3 차원 곡선의 제어점과 끝점을 설명 하는 구조체입니다.

## <a name="cd2dgeometrysinkaddquadraticbeziers"></a><a name="addquadraticbeziers"></a> CD2DGeometrySink:: AddQuadraticBeziers

단일 호출에서 정방형 3 차원 세그먼트의 시퀀스를 배열로 추가 합니다.

```cpp
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>매개 변수

*beziers*<br/>
정방형 3 차원 세그먼트 시퀀스의 배열입니다.

## <a name="cd2dgeometrysinkbeginfigure"></a><a name="beginfigure"></a> CD2DGeometrySink:: BeginFigure

지정 된 지점에서 새 그림을 시작 합니다.

```cpp
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>매개 변수

*점을*<br/>
새 그림을 시작할 지점입니다.

*figureBegin*<br/>
새 그림을 비어 있거나 채워야 하는지 여부입니다.

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="cd2dgeometrysink"></a> CD2DGeometrySink:: CD2DGeometrySink

CD2DPathGeometry 개체에서 CD2DGeometrySink 개체를 생성 합니다.

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>매개 변수

*pathGeometry*<br/>
기존 CD2DPathGeometry 개체입니다.

## <a name="cd2dgeometrysinkclose"></a><a name="close"></a> CD2DGeometrySink:: Close

기 하 도형 싱크를 닫습니다.

```
BOOL Close();
```

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값 그렇지 않으면 FALSE입니다.

## <a name="cd2dgeometrysinkendfigure"></a><a name="endfigure"></a> CD2DGeometrySink:: EndFigure

현재 그림을 종료 합니다. 필요에 따라 닫습니다.

```cpp
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>매개 변수

*figureEnd*<br/>
현재 그림이 닫혀 있는지 여부를 나타내는 값입니다. 그림이 닫혀 있으면 현재 지점과 BeginFigure에서 지정한 시작점 사이에 선이 그려집니다.

## <a name="cd2dgeometrysinkget"></a><a name="get"></a> CD2DGeometrySink:: Get

ID2D1GeometrySink 인터페이스를 반환 합니다.

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>반환 값

ID2D1GeometrySink 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dgeometrysinkisvalid"></a><a name="isvalid"></a> CD2DGeometrySink:: IsValid

기 하 도형 싱크 유효성 검사

```
BOOL IsValid() const;
```

### <a name="return-value"></a>반환 값

Geometry 싱크가 올바르면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cd2dgeometrysinkm_psink"></a><a name="m_psink"></a> CD2DGeometrySink:: m_pSink

ID2D1GeometrySink에 대 한 포인터입니다.

```
ID2D1GeometrySink* m_pSink;
```

## <a name="cd2dgeometrysinkoperator-id2d1geometrysink"></a><a name="operator_id2d1geometrysink_star"></a> CD2DGeometrySink:: operator ID2D1GeometrySink *

ID2D1GeometrySink 인터페이스를 반환 합니다.

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>반환 값

ID2D1GeometrySink 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dgeometrysinksetfillmode"></a><a name="setfillmode"></a> CD2DGeometrySink:: SetFillMode

이 기 하 도형 싱크에 의해 설명 되는 기 하 도형 내에 있는 점과 외부의 위치를 결정 하는 데 사용 되는 메서드를 지정 합니다.

```cpp
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>매개 변수

*fillMode*<br/>
지정 된 점이 기 하 도형의 일부 인지 여부를 확인 하는 데 사용 되는 메서드입니다.

## <a name="cd2dgeometrysinksetsegmentflags"></a><a name="setsegmentflags"></a> CD2DGeometrySink:: SetSegmentFlags

기 하 도형 싱크에 추가 된 새 세그먼트에 적용할 스트로크 및 조인 옵션을 지정 합니다.

```cpp
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>매개 변수

*vertexFlags*<br/>
기 하 도형 싱크에 추가 된 새 세그먼트에 적용할 스트로크 및 조인 옵션입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
