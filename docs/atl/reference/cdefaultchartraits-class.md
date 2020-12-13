---
description: '자세한 정보: CDefaultCharTraits 클래스'
title: CDefaultCharTraits 클래스
ms.date: 11/04/2016
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
ms.openlocfilehash: 6d98c6b6ffb527fef1e5b2320b46eda61ec3f670
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141962"
---
# <a name="cdefaultchartraits-class"></a>CDefaultCharTraits 클래스

이 클래스는 대문자와 소문자 사이에서 문자를 변환 하기 위한 두 개의 정적 함수를 제공 합니다.

## <a name="syntax"></a>구문

```
template <typename T>
class CDefaultCharTraits
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
컬렉션에 저장 되는 데이터의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDefaultCharTraits:: CharToLower](#chartolower)|정적인 문자를 대문자로 변환 하려면이 함수를 호출 합니다.|
|[CDefaultCharTraits:: CharToUpper](#chartoupper)|정적인 문자를 소문자로 변환 하려면이 함수를 호출 합니다.|

## <a name="remarks"></a>설명

이 클래스는 [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)클래스에서 활용 하는 함수를 제공 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="cdefaultchartraitschartolower"></a><a name="chartolower"></a> CDefaultCharTraits:: CharToLower

문자를 소문자로 변환 하려면이 함수를 호출 합니다.

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
소문자로 변환할 문자입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

## <a name="cdefaultchartraitschartoupper"></a><a name="chartoupper"></a> CDefaultCharTraits:: CharToUpper

문자를 대문자로 변환 하려면이 함수를 호출 합니다.

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
대문자로 변환할 문자입니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
