---
description: Boyer_moore_searcher 클래스에 대해 자세히 알아보세요.
title: boyer_moore_searcher 클래스
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_searcher
helpviewer_keywords:
- std::boyer_moore_searcher [C++]
ms.openlocfilehash: 7d8efe145870847aae8e961dad1b4a92fec8bd57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325413"
---
# <a name="boyer_moore_searcher-class"></a>boyer_moore_searcher 클래스

`boyer_moore_searcher`클래스는 Boyer-Moore 알고리즘을 사용 하 여 개체의 생성자에 지정 된 시퀀스를 검색 하는 함수 개체 형식입니다. 검색은 개체의 함수 호출 연산자에 제공 된 다른 시퀀스 내에서 수행 됩니다. 이 클래스는 [std:: search](algorithm-functions.md#search)의 오버 로드 중 하나에 매개 변수로 전달 됩니다.

## <a name="syntax"></a>구문

```cpp
template <
    class RandomAccessIterator1,
    class Hash = hash<typename iterator_traits<RandomAccessIterator1>::value_type>,
    class BinaryPredicate = equal_to<>>
class boyer_moore_searcher
{
    boyer_moore_searcher(
        RandomAccessIterator1 pat_first,
        RandomAccessIterator1 pat_last,
        Hash hf = Hash(),
        BinaryPredicate pred = BinaryPredicate());

    template <class RandomAccessIterator2>
    pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
        RandomAccessIterator2 first,
        RandomAccessIterator2 last) const;
};
```

## <a name="members"></a>멤버

| 멤버 | 설명 |
| - | - |
| **생성자** | |
| [boyer_moore_searcher](#boyer-moore-searcher-constructor) | 검색자 인스턴스를 생성 합니다. |
| **연산자** | |
| [연산자 ()](#operator-call) | 시퀀스에서 작업을 호출 합니다. |

## <a name="boyer_moore_searcher-constructor"></a><a name="boyer-moore-searcher-constructor"></a> boyer_moore_searcher 생성자

`boyer_moore_searcher`검색할 시퀀스, 해시 함수 개체 및 같음 조건자를 사용 하 여 함수 개체를 생성 합니다.

```cpp
boyer_moore_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>매개 변수

*pat_first*\
검색할 시퀀스의 초기 요소입니다.

*pat_last*\
검색할 시퀀스의 끝입니다.

*hf*\
시퀀스 요소를 해시 하는 데 사용 되는 호출 가능 개체입니다.

*pred*\
시퀀스 요소에 대 한 선택적 같음 비교 조건자입니다. 같음 비교 형식이 지정 되지 않은 경우 기본값은 `std::equal_to` 입니다.

### <a name="remarks"></a>설명

*BinaryPredicate*, *hash* 또는 *RandomAccessIterator* 형식의 복사 생성자 또는 *BinaryPredicate* 또는 *hash* 의 호출 연산자에 의해 throw 된 예외를 throw 합니다.

이 클래스는 c + + 17의 새로운 클래스입니다.

## <a name="operator"></a><a name="operator-call"></a> 연산자 ()

함수 개체의 호출 연산자입니다. 인수 시퀀스에서 `[first, last)` 생성자에 지정 된 시퀀스를 검색 합니다.

```cpp
template <class ForwardIterator2>
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
에서 검색할 시퀀스의 초기 요소입니다.

*최신*\
에서 검색할 시퀀스의 끝입니다.

### <a name="remarks"></a>설명

검색 패턴이 비어 있으면 `[pat_first, pat_last)` 를 반환 `make_pair(first, first)` 합니다. 검색 패턴을 찾을 수 없는 경우는를 반환 `make_pair(last, last)` 합니다. 그렇지 않으면는 `[first, last)` 조건자 pred에 따라와 같은에 있는 시퀀스의 시작과 끝에 반복기 쌍을 반환 합니다 `[pat_first, pat_last)` . 

이 클래스는 c + + 17의 새로운 클래스입니다.

## <a name="see-also"></a>참고 항목

[\<functional>](functional.md)\
[알고리즘 함수](algorithm-functions.md)\
[boyer_moore_horspool_searcher 클래스](boyer-moore-horspool-searcher-class.md)\
[std:: search](algorithm-functions.md#search)
