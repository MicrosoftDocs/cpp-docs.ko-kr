---
title: '&lt;random&gt; 함수 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
caps.latest.revision: 10
manager: ghogen
ms.openlocfilehash: e3c5dba462b45589005a996e6226330882b29b15
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt; 함수

## <a name="generate_canonical"></a>  generate_canonical

임의 시퀀스에서 부동 소수점 값을 반환합니다.

> [!NOTE]
> ISO C++ 표준에 따르면 이 함수는 범위 [ `0`, `1`) 내 값을 반환해야 합니다. Visual Studio는 아직 이 제약 조건을 따르고 있지 않습니다. 이 범위에 속하는 값을 생성하려면 [uniform_real_distribution](../standard-library/uniform-real-distribution-class.md)을 사용합니다.

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>매개 변수

`RealType` 부동 소수점 정수 형식입니다. 가능한 형식은 [\<random>](../standard-library/random.md)를 참조하세요.

`Bits` 난수 생성기입니다.

`Gen` 난수 생성기입니다.

### <a name="remarks"></a>설명

템플릿 함수는 `operator()`의 `Gen`를 반복적으로 호출하고 `x`에서 지정한 수의 가수 비트를 수집할 때까지 반환된 값을 `RealType` 형식의 부동 소수점 값 `x`로 압축합니다. 지정된 수는 `Bits`(0이 아니어야 함)와 `RealType`의 전체 가수 비트 수보다 작아야 합니다. 첫 번째 호출은 최하위 비트를 제공합니다. 함수에서 `x`을 반환합니다.

## <a name="see-also"></a>참고자료

[\<random>](../standard-library/random.md)<br/>
