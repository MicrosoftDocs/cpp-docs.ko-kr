---
description: '다음에 대 한 자세한 정보: &lt; hash_set&gt;'
title: '&lt;hash_set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <hash_set>
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
ms.openlocfilehash: aec05414d11bd5312febf4dd61b71db1b3f04452
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98125963"
---
# <a name="lthash_setgt"></a>&lt;hash_set&gt;

> [!NOTE]
> 이 헤더는 사용되지 않습니다. [<unordered_set>](../standard-library/unordered-set.md)을 대신 사용하는 것이 좋습니다.

컨테이너 클래스 템플릿 hash_set 및 hash_multiset 및 해당 지원 템플릿을 정의 합니다.

## <a name="syntax"></a>구문

```cpp
#include <hash_set>
```

## <a name="remarks"></a>설명

### <a name="operators"></a>연산자

|Hash_set 버전|Hash_multiset 버전|설명|
|-----------------------|----------------------------|-----------------|
|[operator! = (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[operator!=(hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|연산자의 좌변에 있는 hash_set 또는 hash_multiset 개체가 우변에 있는 hash_set 또는 hash_multiset 개체와 같지 않은지 테스트합니다.|
|[operator==(hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[operator = = (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|연산자의 좌변에 있는 hash_set 또는 hash_multiset 개체가 우변에 있는 hash_set 또는 hash_multiset 개체와 같은지 테스트합니다.|

### <a name="specialized-template-functions"></a>특별 템플릿 함수

|Hash_set 버전|Hash_multiset 버전|설명|
|-----------------------|----------------------------|-----------------|
|[swap(hash_set)](../standard-library/hash-set-functions.md#swap)|[swap(hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|두 hash_set 또는 hash_multiset의 요소를 교환합니다.|

### <a name="classes"></a>클래스

|클래스|설명|
|-|-|
|[hash_compare 클래스](../standard-library/hash-compare-class.md)|해시 연관 컨테이너 (hash_map, hash_multimap, hash_set 또는 hash_multiset) 중 하나에서 사용할 수 있는 개체에 대해 설명 하 고이 개체에 `Traits` 포함 된 요소를 정렬 하 고 해시 하는 기본 매개 변수 개체로 사용 합니다.|
|[hash_set 클래스](../standard-library/hash-set-class.md)|포함된 요소의 값이 고유하고 키 값으로 사용된 컬렉션의 데이터를 빠르게 검색하고 스토리지하는 데 사용됩니다.|
|[hash_multiset 클래스](../standard-library/hash-multiset-class.md)|포함된 요소의 값이 고유하고 키 값으로 사용된 컬렉션의 데이터를 빠르게 검색하고 스토리지하는 데 사용됩니다.|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
