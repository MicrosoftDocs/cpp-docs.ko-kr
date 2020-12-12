---
description: '자세히 알아보기: CD2DRectU 클래스'
title: CD2DRectU 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
ms.openlocfilehash: dadbaf37f1ed11f96f29c7e4cf78eebf8095590d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301622"
---
# <a name="cd2drectu-class"></a>CD2DRectU 클래스

`D2D1_RECT_U`의 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DRectU:: CD2DRectU](#cd2drectu)|오버로드됨. `CD2DRectU`개체에서 개체를 생성 `D2D1_RECT_U` 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CD2DRectU:: IsNull](#isnull)|식에 유효한 데이터 (NULL)가 포함 되어 있지 않은지 여부를 나타내는 **부울** 값을 반환 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CD2DRectU:: operator CRect](#operator_crect)|`CD2DRectU`개체로 변환 `CRect` 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2drectucd2drectu"></a><a name="cd2drectu"></a> CD2DRectU:: CD2DRectU

CRect 개체에서 CD2DRectU 개체를 생성 합니다.

```
CD2DRectU(const CRect& rect);
CD2DRectU(const D2D1_RECT_U& rect);
CD2DRectU(const D2D1_RECT_U* rect);

CD2DRectU(
    UINT32 uLeft = 0,
    UINT32 uTop = 0,
    UINT32 uRight = 0,
    UINT32 uBottom = 0);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
소스 사각형

*uLeft*<br/>
원본 왼쪽 좌표

*uTop*<br/>
원본 위쪽 좌표

*uRight*<br/>
원본 오른쪽 좌표

*uBottom*<br/>
원본 아래쪽 좌표

## <a name="cd2drectuisnull"></a><a name="isnull"></a> CD2DRectU:: IsNull

식에 유효한 데이터 (Null)가 포함 되어 있지 않은지 여부를 나타내는 부울 값을 반환 합니다.

```
BOOL IsNull() const;
```

### <a name="return-value"></a>반환 값

사각형의 위쪽, 왼쪽, 아래쪽 및 오른쪽 값이 모두 0 이면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cd2drectuoperator-crect"></a><a name="operator_crect"></a> CD2DRectU:: operator CRect

CD2DRectU을 CRect 개체로 변환 합니다.

```
operator CRect();
```

### <a name="return-value"></a>반환 값

D2D 사각형의 현재 값입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
