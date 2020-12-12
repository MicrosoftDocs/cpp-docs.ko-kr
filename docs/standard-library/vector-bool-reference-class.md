---
description: '자세한 정보: vector &lt; bool &gt; :: reference 클래스'
title: vector&lt;bool&gt;::reference 클래스
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 4e9e4700f8af269f02f038c37d55460bae3a2a96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280484"
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference 클래스

`vector<bool>::reference`클래스는 시뮬레이션할 [vector \<bool> 클래스](../standard-library/vector-bool-class.md) 에서 제공 하는 프록시 클래스입니다 `bool&` .

## <a name="remarks"></a>설명

C++는 기본적으로 비트에 직접 참조를 허용하지 않으므로 시뮬레이션된 참조가 필요하지 않습니다. `vector<bool>`는 요소당 1비트만 사용하며, 이 프록시 클래스만 사용하여 참조할 수 있습니다. 하지만, 특정 할당은 유효하지 않으므로 참조 시뮬레이션이 완전하지 않습니다. 예를 들어 개체의 주소를 가져올 수 없기 때문에를 `vector<bool>::reference` 사용 하려고 시도 하는 다음 코드는 `vector<bool>::operator&` 올바르지 않습니다.

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[flip](../standard-library/vector-bool-reference-flip.md)|벡터 요소의 부울 값을 반전합니다.|
|[연산자 bool](../standard-library/vector-bool-reference-operator-bool.md)|에서로의 암시적 변환을 `vector<bool>::reference` 제공 **`bool`** 합니다.|
|[연산자 =](../standard-library/vector-bool-reference-operator-assign.md)|비트에 부울 값을 할당하거나 참조된 요소에 저장된 값을 비트에 할당합니다.|

## <a name="requirements"></a>요구 사항

**헤더**: \<vector>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[\<vector>](../standard-library/vector.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
