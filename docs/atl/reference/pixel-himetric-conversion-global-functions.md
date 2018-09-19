---
title: 픽셀-HIMETRIC 변환 전역 함수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
dev_langs:
- C++
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5ab980813eec09fe0eef35f54280444d8c08b80
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105390"
---
# <a name="pixelhimetric-conversion-global-functions"></a>픽셀/HIMETRIC 변환 전역 함수

이러한 함수를 픽셀 및 HIMETRIC 단위에서 변환에 대 한 지원을 제공 합니다.

> [!IMPORTANT]
>  다음 표에 나열 된 함수를 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|(각 단위는 0.01mm)) HIMETRIC 단위 픽셀로 변환 합니다.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|픽셀 HIMETRIC 단위 변환 (각 단위는 0.01mm)).|

##  <a name="atlhimetrictopixel"></a>  AtlHiMetricToPixel

개체의 HIMETRIC 단위 크기(각 단위는 0.01mm)를 화면 장치의 픽셀 크기로 변환합니다.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric, 
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>매개 변수

*lpSizeInHiMetric*<br/>
[in] 개체의 HIMETRIC 단위 크기에 대 한 포인터입니다.

*lpSizeInPix*<br/>
[out] 반환할 개체의 크기 (픽셀 단위) 인에 대 한 포인터입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]  

### <a name="requirements"></a>요구 사항

**헤더:** atlwin.h

##  <a name="atlpixeltohimetric"></a>  AtlPixelToHiMetric

화면 장치에서 개체의 픽셀 크기를 HIMETRIC 단위의 크기(각 단위는 0.01mm)로 변환합니다.

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix, 
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>매개 변수

*lpSizeInPix*<br/>
[in] 개체의 크기 (픽셀 단위)에 대 한 포인터입니다.

*lpSizeInHiMetric*<br/>
[out] 반환할 개체의 HIMETRIC 단위 크기 인에 대 한 포인터입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]  

### <a name="requirements"></a>요구 사항

**헤더:** atlwin.h  

## <a name="see-also"></a>참고 항목

[함수](../../atl/reference/atl-functions.md)
