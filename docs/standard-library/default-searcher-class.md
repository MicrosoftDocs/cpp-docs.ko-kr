---
title: default_searcher 클래스
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 307fc6da3b383690e0b65bff2a72f386a37d6711
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039692"
---
# <a name="default_searcher-class"></a>default_searcher 클래스

는 `default_searcher` 개체의 생성자에 지정 된 시퀀스를 검색 하는 작업에 대 한 함수 개체 형식입니다. 검색은 개체의 함수 호출 연산자에 제공 된 다른 시퀀스 내에서 수행 됩니다. 는 `default_searcher` [std:: search](algorithm-functions.md#search) 를 호출 하 여 검색을 수행 합니다.

## <a name="syntax"></a>구문

```cpp
template <class ForwardIterator, class BinaryPredicate = equal_to<>>
class default_searcher
{
    default_searcher(
        ForwardIterator pat_first,
        ForwardIterator pat_last,
        BinaryPredicate pred = BinaryPredicate());

    template <class ForwardIterator2>
    pair<ForwardIterator2, ForwardIterator2> operator()(
        ForwardIterator2 first,
        ForwardIterator2 last) const;
};
```

## <a name="members"></a>멤버

| 멤버 | Description |
| - | - |
| **생성자** | |
| [default_searcher](#default-searcher-constructor) | 검색자 인스턴스를 생성 합니다. |
| **연산자** | |
| [연산자 ()](#operator-call) | 시퀀스에서 작업을 호출 합니다. |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a> default_searcher 생성자

`default_searcher`검색할 시퀀스와 같음 조건자를 사용 하 여 함수 개체를 생성 합니다.

```cpp
default_searcher(                   // C++17
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());

constexpr default_searcher(         // C++20
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>매개 변수

*pat_first*\
검색할 시퀀스의 초기 요소입니다.

*pat_last*\
검색할 시퀀스의 끝입니다.

*pred*\
시퀀스 요소에 대 한 선택적 같음 비교 조건자입니다. 같음 비교 형식이 지정 되지 않은 경우 기본값은 `std::equal_to` 입니다.

### <a name="remarks"></a>설명

*BinaryPredicate* 또는 *forwarditerator* 형식의 복사 생성자에서 throw 된 예외를 throw 합니다.

이 클래스는 c + + 17의 새로운 클래스입니다. C + + 20에서 생성자를 만들었습니다 **`constexpr`** .

## <a name="operator"></a><a name="operator-call"></a> 연산자 ()

함수 연산자의 호출 연산자입니다. 인수 시퀀스에서 `[first, last)` 생성자에 지정 된 시퀀스를 검색 합니다.

```cpp
template <class ForwardIterator2>   // C++17
pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;

template <class ForwardIterator2>   // C++20
constexpr pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;
```

### <a name="parameters"></a>매개 변수

*기본*\
에서 검색할 시퀀스의 초기 요소입니다.

*최신*\
에서 검색할 시퀀스의 끝입니다.

### <a name="remarks"></a>설명

반복기 쌍을 반환합니다. 초기 반복기는 다음의 효과적인 *결과입니다.*

`std::search( first, last, pat_first, pat_last, pred )`.

*I**가 *last*인 경우 쌍의 두 번째 반복기는 *마지막* 입니다. 그렇지 않으면 다음의 효과적인 결과입니다.

`std::next( i, std::distance( pat_first, pat_last ))`.

이 클래스는 c + + 17의 새로운 클래스입니다. C + + 20에서 호출 연산자를 만들었습니다 **`constexpr`** .

## <a name="see-also"></a>참고 항목

[\<functional>](functional.md)\
[알고리즘 함수](algorithm-functions.md)\
[std:: search](algorithm-functions.md#search)
