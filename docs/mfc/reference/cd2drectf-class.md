---
description: '자세히 알아보기: CD2DRectF 클래스'
title: CD2DRectF 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 273a3d07f152f8b24a24175c0f466c8969830ebd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136021"
---
# <a name="cd2drectf-class"></a>CD2DRectF 클래스

`D2D1_RECT_F`의 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DRectF:: CD2DRectF](#cd2drectf)|오버로드됨. `CD2DRectF`개체에서 개체를 생성 `D2D1_RECT_F` 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DRectF:: IsNull](#isnull)|식에 유효한 데이터 (NULL)가 포함 되어 있지 않은지 여부를 나타내는 **부울** 값을 반환 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DRectF:: operator CRect](#operator_crect)|`CD2DRectF`개체로 변환 `CRect` 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2drectfcd2drectf"></a><a name="cd2drectf"></a> CD2DRectF:: CD2DRectF

CRect 개체에서 CD2DRectF 개체를 생성 합니다.

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
소스 사각형

*왼쪽*<br/>
원본 왼쪽 좌표

*fTop*<br/>
원본 위쪽 좌표

*fRight*<br/>
원본 오른쪽 좌표

*fBottom*<br/>
원본 아래쪽 좌표

## <a name="cd2drectfisnull"></a><a name="isnull"></a> CD2DRectF:: IsNull

식에 유효한 데이터 (Null)가 포함 되어 있지 않은지 여부를 나타내는 부울 값을 반환 합니다.

```
BOOL IsNull() const;
```

### <a name="return-value"></a>반환 값

사각형의 위쪽, 왼쪽, 아래쪽 및 오른쪽 값이 모두 0 이면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cd2drectfoperator-crect"></a><a name="operator_crect"></a> CD2DRectF:: operator CRect

CD2DRectF을 CRect 개체로 변환 합니다.

```
operator CRect();
```

### <a name="return-value"></a>반환 값

D2D 사각형의 현재 값입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
