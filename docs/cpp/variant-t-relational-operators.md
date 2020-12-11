---
description: '다음에 대 한 자세한 정보: _variant_t 관계형 연산자'
title: _variant_t 관계형 연산자
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
ms.openlocfilehash: 0a9c339bc67527e258c0d1f69060cde251c8adb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161431"
---
# <a name="_variant_t-relational-operators"></a>_variant_t 관계형 연산자

**Microsoft 전용**

두 `_variant_t` 개체가 같음 또는 같지 않음을 비교합니다.

## <a name="syntax"></a>구문

```
bool operator==(
   const VARIANT& varSrc) const;
bool operator==(
   const VARIANT* pSrc) const;
bool operator!=(
   const VARIANT& varSrc) const;
bool operator!=(
   const VARIANT* pSrc) const;
```

#### <a name="parameters"></a>매개 변수

*varSrc*<br/>
`VARIANT`개체와 비교할 `_variant_t` 입니다.

*.Psrc*<br/>
개체와 비교할에 대 한 포인터 `VARIANT` `_variant_t` 입니다.

## <a name="return-value"></a>반환 값

**`true`** 비교가 포함 되 면를 반환 하 고, 그렇지 않으면를 반환 **`false`** 합니다.

## <a name="remarks"></a>설명

개체를과 비교 `_variant_t` `VARIANT` 하 여 같은지 또는 같지 않은지 테스트 합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_variant_t 클래스](../cpp/variant-t-class.md)
