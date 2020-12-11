---
description: '자세히 알아보기: &lt; 임의 &gt; 함수'
title: '&lt;random&gt; 함수'
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 39670fcd9b200a6bd56656bbfa07391fdd0d96be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163342"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt; 함수

## <a name="generate_canonical"></a><a name="generate_canonical"></a> generate_canonical

임의 시퀀스에서 부동 소수점 값을 반환합니다.

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>매개 변수

*RealType*\
부동 소수점 정수 형식입니다. 가능한 형식은를 참조 하십시오 [\<random>](../standard-library/random.md) .

*비트씩*\
사용할 임의성의 비트 수입니다.

*생성기*\
난수 생성기 클래스입니다.

*차세대*\
형식 *생성기* 의 난수 생성기의 인스턴스에 대 한 참조입니다.

### <a name="remarks"></a>설명

템플릿 함수는 `operator()` *Gen* 를 반복적으로 호출 하 고 `x` 에서 지정한 수의가 수 비트를 수집할 때까지 반환 된 값을 *RealType* 형식의 부동 소수점 값으로 압축 합니다 `x` . 지정 된 숫자는 *비트* (0이 아니어야 함)와 *RealType* 의 전체가 수 비트 수의 보다 작은 숫자입니다. 첫 번째 호출은 최하위 비트를 제공합니다. 함수에서 `x`을 반환합니다.
