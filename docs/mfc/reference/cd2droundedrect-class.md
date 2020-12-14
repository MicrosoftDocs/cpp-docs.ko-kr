---
description: '자세히 알아보기: CD2DRoundedRect 클래스'
title: CD2DRoundedRect 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect::CD2DRoundedRect
helpviewer_keywords:
- CD2DRoundedRect [MFC], CD2DRoundedRect
ms.assetid: 06207fb5-e92b-41c0-bceb-b45d8f466531
ms.openlocfilehash: 13c1b0910c9d78f615d64e3eecba8bb813916413
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240665"
---
# <a name="cd2droundedrect-class"></a>CD2DRoundedRect 클래스

`D2D1_ROUNDED_RECT`의 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DRoundedRect : public D2D1_ROUNDED_RECT;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DRoundedRect:: CD2DRoundedRect](#cd2droundedrect)|오버로드됨. `CD2DRoundedRect`개체에서 개체를 생성 `D2D1_ROUNDED_RECT` 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`D2D1_ROUNDED_RECT`

[CD2DRoundedRect](../../mfc/reference/cd2droundedrect-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2droundedrectcd2droundedrect"></a><a name="cd2droundedrect"></a> CD2DRoundedRect:: CD2DRoundedRect

CD2DRectF 개체에서 CD2DRoundedRect 개체를 생성 합니다.

```
CD2DRoundedRect(
    const CD2DRectF& rectIn,
    const CD2DSizeF& sizeRadius);

CD2DRoundedRect(const D2D1_ROUNDED_RECT& rectIn);
CD2DRoundedRect(const D2D1_ROUNDED_RECT* rectIn);
```

### <a name="parameters"></a>매개 변수

*rectIn*<br/>
소스 사각형

*sizeRadius*<br/>
반경 크기

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
