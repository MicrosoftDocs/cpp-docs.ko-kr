---
description: '자세히 알아보기: CD2DEllipse 클래스'
title: CD2DEllipse 클래스
ms.date: 08/29/2019
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
ms.openlocfilehash: 827ba5515cb4b20cb8e5b10012590a001e01c08f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313062"
---
# <a name="cd2dellipse-class"></a>CD2DEllipse 클래스

`D2D1_ELLIPSE`의 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DEllipse : public D2D1_ELLIPSE;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DEllipse:: CD2DEllipse](#cd2dellipse)|오버로드됨. `CD2DEllipse`개체에서 개체를 생성 `D2D1_ELLIPSE` 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dellipsecd2dellipse"></a><a name="cd2dellipse"></a> CD2DEllipse:: CD2DEllipse

CD2DRectF 개체에서 CD2DEllipse 개체를 생성 합니다.

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
CD2DEllipse(const D2D1_ELLIPSE* ellipse);

CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
소스 사각형

*타원형*<br/>
원본 타원

*ptCenter*<br/>
타원의 중심점입니다.

*sizeRadius*<br/>
타원의 X 반지름 및 Y 반경입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
