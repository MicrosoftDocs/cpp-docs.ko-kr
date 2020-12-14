---
description: '자세히 알아보기: CD2DGeometry 클래스'
title: CD2DGeometry 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::Attach
- AFXRENDERTARGET/CD2DGeometry::CombineWithGeometry
- AFXRENDERTARGET/CD2DGeometry::CompareWithGeometry
- AFXRENDERTARGET/CD2DGeometry::ComputeArea
- AFXRENDERTARGET/CD2DGeometry::ComputeLength
- AFXRENDERTARGET/CD2DGeometry::ComputePointAtLength
- AFXRENDERTARGET/CD2DGeometry::Destroy
- AFXRENDERTARGET/CD2DGeometry::Detach
- AFXRENDERTARGET/CD2DGeometry::FillContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Get
- AFXRENDERTARGET/CD2DGeometry::GetBounds
- AFXRENDERTARGET/CD2DGeometry::GetWidenedBounds
- AFXRENDERTARGET/CD2DGeometry::IsValid
- AFXRENDERTARGET/CD2DGeometry::Outline
- AFXRENDERTARGET/CD2DGeometry::Simplify
- AFXRENDERTARGET/CD2DGeometry::StrokeContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Tessellate
- AFXRENDERTARGET/CD2DGeometry::Widen
- AFXRENDERTARGET/CD2DGeometry::m_pGeometry
helpviewer_keywords:
- CD2DGeometry [MFC], CD2DGeometry
- CD2DGeometry [MFC], Attach
- CD2DGeometry [MFC], CombineWithGeometry
- CD2DGeometry [MFC], CompareWithGeometry
- CD2DGeometry [MFC], ComputeArea
- CD2DGeometry [MFC], ComputeLength
- CD2DGeometry [MFC], ComputePointAtLength
- CD2DGeometry [MFC], Destroy
- CD2DGeometry [MFC], Detach
- CD2DGeometry [MFC], FillContainsPoint
- CD2DGeometry [MFC], Get
- CD2DGeometry [MFC], GetBounds
- CD2DGeometry [MFC], GetWidenedBounds
- CD2DGeometry [MFC], IsValid
- CD2DGeometry [MFC], Outline
- CD2DGeometry [MFC], Simplify
- CD2DGeometry [MFC], StrokeContainsPoint
- CD2DGeometry [MFC], Tessellate
- CD2DGeometry [MFC], Widen
- CD2DGeometry [MFC], m_pGeometry
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
ms.openlocfilehash: 2c902554ba5377ce9f7a4a481d4001a9ef7a47f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193450"
---
# <a name="cd2dgeometry-class"></a>CD2DGeometry 클래스

ID2D1Geometry에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DGeometry:: CD2DGeometry](#cd2dgeometry)|CD2DGeometry 개체를 생성 합니다.|
|[CD2DGeometry:: ~ CD2DGeometry](#_dtorcd2dgeometry)|소멸자입니다. D2D geometry 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DGeometry:: Attach](#attach)|기존 리소스 인터페이스를 개체에 연결 합니다.|
|[CD2DGeometry:: CombineWithGeometry](#combinewithgeometry)|이 geometry를 지정 된 기 하 도형으로 결합 하 고 결과를 ID2D1SimplifiedGeometrySink에 저장 합니다.|
|[CD2DGeometry:: CompareWithGeometry](#comparewithgeometry)|이 geometry와 지정 된 기 하 도형의 교차를 설명 합니다. 지정 된 평면화 허용 오차를 사용 하 여 비교가 수행 됩니다.|
|[CD2DGeometry:: Earea](#computearea)|지정 된 매트릭스에 의해 변환 되 고 지정 된 허용 오차를 사용 하 여 평면화 된 후에 기 하 도형의 면적을 계산 합니다.|
|[CD2DGeometry:: ComputeLength](#computelength)|각 세그먼트가 선으로 unrolled는 것 처럼 기 하 도형 길이를 계산 합니다.|
|[CD2DGeometry:: Epointatlength](#computepointatlength)|지정 된 매트릭스에 의해 변환 되 고 지정 된 허용 오차를 사용 하 여 평면화 된 후에 기 하 도형에 따라 지정 된 거리 만큼 지점 및 탄젠트 벡터를 계산 합니다.|
|[CD2DGeometry::D estroy](#destroy)|CD2DGeometry 개체를 소멸 시킵니다. [CD2DResource::D estroy](../../mfc/reference/cd2dresource-class.md#destroy)를 재정의 합니다.|
|[CD2DGeometry::D etach](#detach)|개체에서 리소스 인터페이스를 분리 합니다.|
|[CD2DGeometry:: FillContainsPoint](#fillcontainspoint)|지정 된 평면화 허용 오차를 지정 하 여 기 하 도형에 의해 채워진 영역에 지정 된 점이 포함 되는지 여부를 나타냅니다.|
|[CD2DGeometry:: Get](#get)|ID2D1Geometry 인터페이스를 반환 합니다.|
|[CD2DGeometry:: GetBounds](#getbounds)||
|[CD2DGeometry:: GetWidenedBounds](#getwidenedbounds)|지정 된 스트로크 너비와 스타일로 확장 되 고 지정 된 매트릭스에 의해 변환 된 후의 기 하 도형 경계를 가져옵니다.|
|[CD2DGeometry:: IsValid](#isvalid)|리소스 유효성 검사 ( [CD2DResource:: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)재정의)|
|[CD2DGeometry:: 윤곽선](#outline)|기 하 도형의 윤곽선을 계산 하 고 결과를 ID2D1SimplifiedGeometrySink에 씁니다.|
|[CD2DGeometry:: 간소화](#simplify)|선 및 (선택 사항) 입방 형 3 차원 곡선만 포함 하 고 결과를 ID2D1SimplifiedGeometrySink에 쓰는 단순화 된 버전의 기 하 도형을 만듭니다.|
|[CD2DGeometry:: StrokeContainsPoint](#strokecontainspoint)|지정 된 스트로크 두께, 스타일 및 변환이 지정 된 경우 기 하 도형 스트로크에 지정 된 점이 포함 되어 있는지 여부를 확인 합니다.|
|[CD2DGeometry:: 개수가 계산 되](#tessellate)|지정한 행렬을 사용하여 변환되고 지정한 허용 오차를 사용하여 평면화된 기하 도형을 포괄하는 시계 방향으로 돌아가는 삼각형 집합을 만듭니다.|
|[CD2DGeometry:: 넓히기](#widen)|지정 된 브러쉬로 기 하 도형를 확대 하 고 지정 된 행렬에 의해 변환 되 고 지정 된 허용 오차를 사용 하 여 평면화 된 후 결과를 ID2D1SimplifiedGeometrySink에 씁니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DGeometry:: operator ID2D1Geometry *](#operator_id2d1geometry_star)|ID2D1Geometry 인터페이스를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CD2DGeometry:: m_pGeometry](#m_pgeometry)|ID2D1Geometry에 대 한 포인터입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dgeometrycd2dgeometry"></a><a name="_dtorcd2dgeometry"></a> CD2DGeometry:: ~ CD2DGeometry

소멸자입니다. D2D geometry 개체가 제거 될 때 호출 됩니다.

```
virtual ~CD2DGeometry();
```

## <a name="cd2dgeometryattach"></a><a name="attach"></a> CD2DGeometry:: Attach

기존 리소스 인터페이스를 개체에 연결 합니다.

```cpp
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>매개 변수

*보도 Ource*<br/>
기존 리소스 인터페이스입니다. NULL 일 수 없음

## <a name="cd2dgeometrycd2dgeometry"></a><a name="cd2dgeometry"></a> CD2DGeometry:: CD2DGeometry

CD2DGeometry 개체를 생성 합니다.

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*pParentTarget*<br/>
렌더링 대상에 대 한 포인터입니다.

*bAutoDestroy*<br/>
개체가 소유자 (pParentTarget)에 의해 소멸 됨을 나타냅니다.

## <a name="cd2dgeometrycombinewithgeometry"></a><a name="combinewithgeometry"></a> CD2DGeometry:: CombineWithGeometry

이 geometry를 지정 된 기 하 도형으로 결합 하 고 결과를 ID2D1SimplifiedGeometrySink에 저장 합니다.

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>매개 변수

*inputGeometry*<br/>
이 인스턴스와 결합할 기 하 도형입니다.

*combineMode*<br/>
수행할 조합 작업의 형식입니다.

*inputGeometryTransform*<br/>
결합 하기 전에 inputGeometry에 적용할 변환입니다.

*geometrySink*<br/>
결합 작업의 결과입니다.

*flatteningTolerance*<br/>
기하 도형의 다각형 근사에서 각 점들 사이의 거리에 허용되는 최대 범위입니다. 값이 작을수록 결과가 정확해지지만 실행 속도는 느려집니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cd2dgeometrycomparewithgeometry"></a><a name="comparewithgeometry"></a> CD2DGeometry:: CompareWithGeometry

이 geometry와 지정 된 기 하 도형의 교차를 설명 합니다. 지정 된 평면화 허용 오차를 사용 하 여 비교가 수행 됩니다.

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>매개 변수

*inputGeometry*<br/>
테스트할 기 하 도형입니다.

*inputGeometryTransform*<br/>
InputGeometry에 적용할 변환입니다.

*flatteningTolerance*<br/>
기하 도형의 다각형 근사에서 각 점들 사이의 거리에 허용되는 최대 범위입니다. 값이 작을수록 결과가 정확해지지만 실행 속도는 느려집니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cd2dgeometrycomputearea"></a><a name="computearea"></a> CD2DGeometry:: Earea

지정 된 매트릭스에 의해 변환 되 고 지정 된 허용 오차를 사용 하 여 평면화 된 후에 기 하 도형의 면적을 계산 합니다.

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>매개 변수

*worldTransform*<br/>
영역을 계산 하기 전에이 기 하 도형에 적용할 변환입니다.

*면적*<br/>
이 메서드는 반환 될 때이 기 하 도형의 변환 된 평면화 된 버전 영역에 대 한 포인터를 포함 합니다. 이 매개 변수에 대 한 저장소를 할당 해야 합니다.

*flatteningTolerance*<br/>
기하 도형의 다각형 근사에서 각 점 사이의 거리에 허용되는 최대 범위입니다. 값이 작을수록 결과가 정확해지지만 실행 속도는 느려집니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cd2dgeometrycomputelength"></a><a name="computelength"></a> CD2DGeometry:: ComputeLength

각 세그먼트가 선으로 unrolled는 것 처럼 기 하 도형 길이를 계산 합니다.

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>매개 변수

*worldTransform*<br/>
길이를 계산 하기 전에 기 하 도형에 적용할 변환입니다.

*length*<br/>
이 메서드가 반환 될 때 geometry의 길이에 대 한 포인터를 포함 합니다. 폐쇄형 기 하 도형의 경우 길이에는 암시적 닫는 세그먼트가 포함 됩니다. 이 매개 변수에 대 한 저장소를 할당 해야 합니다.

*flatteningTolerance*<br/>
기하 도형의 다각형 근사에서 각 점 사이의 거리에 허용되는 최대 범위입니다. 값이 작을수록 결과가 정확해지지만 실행 속도는 느려집니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cd2dgeometrycomputepointatlength"></a><a name="computepointatlength"></a> CD2DGeometry:: Epointatlength

지정 된 매트릭스에 의해 변환 되 고 지정 된 허용 오차를 사용 하 여 평면화 된 후에 기 하 도형에 따라 지정 된 거리 만큼 지점 및 탄젠트 벡터를 계산 합니다.

```
BOOL ComputePointAtLength(
    FLOAT length,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DPointF& point,
    CD2DPointF& unitTangentVector,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>매개 변수

*length*<br/>
찾을 점 및 탄젠트의 기 하 도형에 따른 거리입니다. 이 거리가 0 보다 낮으면이 메서드는 기 하 도형의 첫 번째 점을 계산 합니다. 이 거리가 기 하 도형의 길이 보다 크면이 메서드는 기 하 도형의 마지막 점을 계산 합니다.

*worldTransform*<br/>
지정 된 지점과 탄젠트를 계산 하기 전에 기 하 도형에 적용할 변환입니다.

*까지*<br/>
Geometry를 따라 지정 된 거리에 있는 위치입니다. 기 하 도형이 비어 있으면이 점에 x 및 y 값이 포함 된 NaN이 포함 됩니다.

*unitTangentVector*<br/>
이 메서드는 반환 될 때 기 하 도형에 따라 지정 된 거리에 있는 탄젠트 벡터에 대 한 포인터를 포함 합니다. 기 하 도형이 비어 있는 경우이 벡터는 x 및 y 값으로 NaN을 포함 합니다. 이 매개 변수에 대 한 저장소를 할당 해야 합니다.

*flatteningTolerance*<br/>
기하 도형의 다각형 근사에서 각 점 사이의 거리에 허용되는 최대 범위입니다. 값이 작을수록 결과가 정확해지지만 실행 속도는 느려집니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cd2dgeometrydestroy"></a><a name="destroy"></a> CD2DGeometry::D estroy

CD2DGeometry 개체를 소멸 시킵니다.

```
virtual void Destroy();
```

## <a name="cd2dgeometrydetach"></a><a name="detach"></a> CD2DGeometry::D etach

개체에서 리소스 인터페이스를 분리 합니다.

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>반환 값

분리 된 리소스 인터페이스에 대 한 포인터입니다.

## <a name="cd2dgeometryfillcontainspoint"></a><a name="fillcontainspoint"></a> CD2DGeometry:: FillContainsPoint

지정 된 평면화 허용 오차를 지정 하 여 기 하 도형에 의해 채워진 영역에 지정 된 점이 포함 되는지 여부를 나타냅니다.

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
테스트할 점입니다.

*worldTransform*<br/>
포함을 테스트 하기 전에 기 하 도형에 적용할 변환입니다.

*contains*<br/>
이 메서드가 반환 될 때 기 하 도형에 의해 채워진 영역에 점이 포함 되 면 TRUE 인 부울 값이 포함 됩니다. 그렇지 않으면 FALSE입니다. 이 매개 변수에 대 한 저장소를 할당 해야 합니다.

*flatteningTolerance*<br/>
정확한 기하학적 경로와 경로 교차점을 계산 하는 데 사용 되는 숫자 정확도입니다. 허용 오차 보다 작은 채우기가 없는 요소는 여전히 내에서 고려 됩니다. 값이 작을수록 결과가 정확해지지만 실행 속도는 느려집니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cd2dgeometryget"></a><a name="get"></a> CD2DGeometry:: Get

ID2D1Geometry 인터페이스를 반환 합니다.

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>반환 값

ID2D1Geometry 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dgeometrygetbounds"></a><a name="getbounds"></a> CD2DGeometry:: GetBounds

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>매개 변수

*worldTransform*<br/>
*범위*

### <a name="return-value"></a>반환 값

## <a name="cd2dgeometrygetwidenedbounds"></a><a name="getwidenedbounds"></a> CD2DGeometry:: GetWidenedBounds

지정 된 스트로크 너비와 스타일로 확장 되 고 지정 된 매트릭스에 의해 변환 된 후의 기 하 도형 경계를 가져옵니다.

```
BOOL GetWidenedBounds(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DRectF& bounds,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>매개 변수

*strokeWidth*<br/>
윤곽선을 스트로크 하 여 기 하 도형을 확장할 크기입니다.

*strokeStyle*<br/>
기 하 도형을 확대 하는 스트로크의 스타일입니다.

*worldTransform*<br/>
기 하 도형이 변형 되 고 형상이 스트로크 된 후에 기 하 도형에 적용할 변환입니다.

*범위*<br/>
이 메서드가 반환 될 때 확장 된 기 하 도형의 경계를 포함 합니다. 이 매개 변수에 대 한 저장소를 할당 해야 합니다.

*flatteningTolerance*<br/>
기하 도형의 다각형 근사에서 각 점들 사이의 거리에 허용되는 최대 범위입니다. 값이 작을수록 결과가 정확해지지만 실행 속도는 느려집니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cd2dgeometryisvalid"></a><a name="isvalid"></a> CD2DGeometry:: IsValid

리소스 유효성 검사

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>반환 값

리소스가 올바르면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cd2dgeometrym_pgeometry"></a><a name="m_pgeometry"></a> CD2DGeometry:: m_pGeometry

ID2D1Geometry에 대 한 포인터입니다.

```
ID2D1Geometry* m_pGeometry;
```

## <a name="cd2dgeometryoperator-id2d1geometry"></a><a name="operator_id2d1geometry_star"></a> CD2DGeometry:: operator ID2D1Geometry *

ID2D1Geometry 인터페이스를 반환 합니다.

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>반환 값

ID2D1Geometry 인터페이스에 대 한 포인터 이거나, 개체가 아직 초기화 되지 않은 경우 NULL입니다.

## <a name="cd2dgeometryoutline"></a><a name="outline"></a> CD2DGeometry:: 윤곽선

기 하 도형의 윤곽선을 계산 하 고 결과를 ID2D1SimplifiedGeometrySink에 씁니다.

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>매개 변수

*worldTransform*<br/>
기 하 도형 윤곽선에 적용할 변환입니다.

*geometrySink*<br/>
기 하 도형 변환 윤곽선이 추가 되는 ID2D1SimplifiedGeometrySink입니다.

*flatteningTolerance*<br/>
기하 도형의 다각형 근사에서 각 점 사이의 거리에 허용되는 최대 범위입니다. 값이 작을수록 결과가 정확해지지만 실행 속도는 느려집니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cd2dgeometrysimplify"></a><a name="simplify"></a> CD2DGeometry:: 간소화

선 및 (선택 사항) 입방 형 3 차원 곡선만 포함 하 고 결과를 ID2D1SimplifiedGeometrySink에 쓰는 단순화 된 버전의 기 하 도형을 만듭니다.

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>매개 변수

*simplificationOption*<br/>
단순화 된 기 하 도형에 곡선이 포함 되어야 하는지 여부를 지정 하는 값입니다.

*worldTransform*<br/>
단순화 된 기 하 도형에 적용할 변환입니다.

*geometrySink*<br/>
단순화 된 기 하 도형을 추가할 ID2D1SimplifiedGeometrySink입니다.

*flatteningTolerance*<br/>
기하 도형의 다각형 근사에서 각 점 사이의 거리에 허용되는 최대 범위입니다. 값이 작을수록 결과가 정확해지지만 실행 속도는 느려집니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cd2dgeometrystrokecontainspoint"></a><a name="strokecontainspoint"></a> CD2DGeometry:: StrokeContainsPoint

지정 된 스트로크 두께, 스타일 및 변환이 지정 된 경우 기 하 도형 스트로크에 지정 된 점이 포함 되어 있는지 여부를 확인 합니다.

```
BOOL StrokeContainsPoint(
    CD2DPointF point,
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
포함 여부를 테스트할 점입니다.

*strokeWidth*<br/>
적용할 스트로크의 두께입니다.

*strokeStyle*<br/>
적용할 스트로크의 스타일입니다.

*worldTransform*<br/>
스트로크 기 하 도형에 적용할 변환입니다.

*contains*<br/>
이 메서드가 반환 될 때 기 하 도형에 지정 된 점이 포함 되어 있으면 TRUE로 설정 된 부울 값이 포함 됩니다. 그렇지 않으면 FALSE입니다. 이 매개 변수에 대 한 저장소를 할당 해야 합니다.

*flatteningTolerance*<br/>
정확한 기하학적 경로와 경로 교차점을 계산 하는 데 사용 되는 숫자 정확도입니다. 스트로크는 허용 오차 보다 작은 것으로 간주 됩니다. 값이 작을수록 결과가 정확해지지만 실행 속도는 느려집니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cd2dgeometrytessellate"></a><a name="tessellate"></a> CD2DGeometry:: 개수가 계산 되

지정한 행렬을 사용하여 변환되고 지정한 허용 오차를 사용하여 평면화된 기하 도형을 포괄하는 시계 방향으로 돌아가는 삼각형 집합을 만듭니다.

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>매개 변수

*worldTransform*<br/>
이 기 하 도형에 적용할 변환 이거나 NULL입니다.

*tessellationSink*<br/>
공간 분할가 추가 되는 ID2D1TessellationSink입니다.

*flatteningTolerance*<br/>
기하 도형의 다각형 근사에서 각 점 사이의 거리에 허용되는 최대 범위입니다. 값이 작을수록 결과가 정확해지지만 실행 속도는 느려집니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cd2dgeometrywiden"></a><a name="widen"></a> CD2DGeometry:: 넓히기

지정 된 브러쉬로 기 하 도형를 확대 하 고 지정 된 행렬에 의해 변환 되 고 지정 된 허용 오차를 사용 하 여 평면화 된 후 결과를 ID2D1SimplifiedGeometrySink에 씁니다.

```
BOOL Widen(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>매개 변수

*strokeWidth*<br/>
기 하 도형을 확장할 크기입니다.

*strokeStyle*<br/>
기 하 도형에 적용할 스트로크의 스타일 이거나 NULL입니다.

*worldTransform*<br/>
기 하 도형을 확장 한 후 기 하 도형에 적용할 변환입니다.

*geometrySink*<br/>
확장 된 기 하 도형을 추가할 ID2D1SimplifiedGeometrySink입니다.

*flatteningTolerance*<br/>
기하 도형의 다각형 근사에서 각 점 사이의 거리에 허용되는 최대 범위입니다. 값이 작을수록 결과가 정확해지지만 실행 속도는 느려집니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
