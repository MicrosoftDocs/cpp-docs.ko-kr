---
title: hash_compare 클래스
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_compare
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
ms.openlocfilehash: 4fb44a371630a66275f6ef59a0bf66b4cb73a71f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689556"
---
# <a name="hash_compare-class"></a>hash_compare 클래스

클래스 템플릿에서는 해시 연관 컨테이너 (hash_map, hash_multimap, hash_set 또는 hash_multiset) 중 하나에서 사용할 수 있는 개체를 설명 하 고이 개체에 포함 된 요소를 정렬 하 고 해시 하는 기본 **특성** 매개 변수 개체로 사용할 수 있습니다.

## <a name="syntax"></a>구문

class hash_compare { Traits comp; public: const size_t bucket_size = 4; const size_t min_buckets = 8; hash_compare(); hash_compare(Traits pred); size_t operator()(const Key& key) const; bool operator()( const Key& key1, const Key& key2) const; };

## <a name="remarks"></a>주의

각 해시 연관 컨테이너는 `Traits` (템플릿 매개 변수) 형식의 해시 특성 개체를 저장 합니다. hash_compare 특수화에서 클래스를 파생시켜 특정 함수 및 개체를 선택적으로 재정의하거나, 최소한의 특정 요구를 충족하는 경우 이 클래스의 고유한 버전을 제공할 수 있습니다. 특히 `hash_compare<Key, Traits>` 형식의 hash_comp 개체의 경우 위의 컨테이너에서 다음과 같은 동작을 수행 해야 합니다.

- @No__t_1 형식 `key` 모든 값에 대해 호출 **hash_comp**(`key`)는 `size_t` 형식의 값 분포를 생성 하는 해시 함수 역할을 합니다. hash_compare에서 제공하는 함수는 `key`를 반환합니다.

- 시퀀스의 `key2` 앞에 `key1` 해시 함수에서 반환 되는 값과 동일한 해시 값 (해시 함수에서 반환 되는 값)을 가진 형식의 `Key` 형식에 대 한 값이 false 인 경우 **hash_comp**(`key2`, `key1`)는 false입니다. 함수는 `Key` 형식의 값에 전체 순서 지정을 적용 해야 합니다. Hash_compare에서 제공 하는 함수는 *comp*(`key2`, `key1`) `,`를 반환 합니다. 여기서 *comp* 는 hash_comp 개체를 생성할 때 지정할 수 있는 `Traits` 형식의 저장 된 개체입니다. 기본 `Traits` 매개 변수 형식 `less<Key>`의 경우 정렬 키가 값으로 감소 하지 않습니다.

- 정수 상수 `bucket_size` 컨테이너가 초과 하지 않아야 하는 "버킷" (해시 테이블 항목) 당 평균 요소 수를 지정 합니다. 0보다 커야 합니다. hash_compare에서 제공하는 값은 4입니다.

- 해시 테이블에서 유지할 최소 버킷 수를 지정 하는 정수 상수 `min_buckets`입니다. 0보다 큰 2의 거듭제곱이어야 합니다. hash_compare에서 제공하는 값은 8입니다.

## <a name="example"></a>예제

hash_compare를 선언 및 사용하는 방법의 예제는 [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map), [hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap), [hash_set::hash_set](../standard-library/hash-set-class.md#hash_set) 및 [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset)에 대한 예제를 참조하세요.

## <a name="requirements"></a>요구 사항

**헤더:** \<hash_map>

**네임스페이스:** stdext

## <a name="see-also"></a>참조

[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
