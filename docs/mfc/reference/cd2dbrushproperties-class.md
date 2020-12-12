---
description: '자세히 알아보기: CD2DBrushProperties 클래스'
title: CD2DBrushProperties 클래스
ms.date: 11/04/2016
f1_keywords:
- CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CommonInit
helpviewer_keywords:
- CD2DBrushProperties [MFC], CD2DBrushProperties
- CD2DBrushProperties [MFC], CommonInit
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
ms.openlocfilehash: d16d08041b5096c8a5ad188201c6a06e21681849
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227561"
---
# <a name="cd2dbrushproperties-class"></a>CD2DBrushProperties 클래스

`D2D1_BRUSH_PROPERTIES`의 래퍼입니다.

## <a name="syntax"></a>구문

```
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CD2DBrushProperties:: CD2DBrushProperties](#cd2dbrushproperties)|오버로드됨. 구조체를 만듭니다. `CD2D_BRUSH_PROPERTIES`|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CD2DBrushProperties:: CommonInit](#commoninit)|개체를 초기화 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>요구 사항

**헤더:** afxrendertarget

## <a name="cd2dbrushpropertiescd2dbrushproperties"></a><a name="cd2dbrushproperties"></a> CD2DBrushProperties:: CD2DBrushProperties

CD2D_BRUSH_PROPERTIES 구조체를 만듭니다.

```
CD2DBrushProperties();
CD2DBrushProperties(FLOAT _opacity);

CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,
    FLOAT _opacity = 1.);
```

### <a name="parameters"></a>매개 변수

*_opacity*<br/>
브러시의 기본 불투명도입니다. 기본값은 1.0입니다.

*_transform*<br/>
브러시에 적용할 변환입니다.

## <a name="cd2dbrushpropertiescommoninit"></a><a name="commoninit"></a> CD2DBrushProperties:: CommonInit

개체를 초기화 합니다.

```cpp
void CommonInit();
```

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
