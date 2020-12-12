---
description: '자세히 알아보기: CD2DPointF 클래스'
title: CD2DPointF 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
ms.openlocfilehash: 0f63aa35acb33504c96316b67ecc4f885f4f0247
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193359"
---
# <a name="cd2dpointf-class"></a>CD2DPointF 클래스

`D2D1_POINT_2F`의 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DPointF : public D2D1_POINT_2F;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DPointF:: CD2DPointF](#cd2dpointf)|오버로드됨. `CD2DPointF`개체에서 개체를 생성 `D2D1_POINT_2F` 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DPointF:: operator CPoint](#operator_cpoint)|`CD2DPointF`개체로 변환 `CPoint` 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dpointfcd2dpointf"></a><a name="cd2dpointf"></a> CD2DPointF:: CD2DPointF

CPoint 개체에서 CD2DPointF 개체를 생성 합니다.

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>매개 변수

*pt*<br/>
원본 지점

*fX*<br/>
원본 X

*연도로*<br/>
원본 Y

## <a name="cd2dpointfoperator-cpoint"></a><a name="operator_cpoint"></a> CD2DPointF:: operator CPoint

CD2DPointF를 CPoint 개체로 변환 합니다.

```
operator CPoint();
```

### <a name="return-value"></a>반환 값

D2D 지점의 현재 값입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
