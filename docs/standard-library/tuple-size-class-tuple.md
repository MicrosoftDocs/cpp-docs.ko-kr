---
description: '다음에 대 한 자세한 정보: tuple_size 클래스;'
title: tuple_size 클래스
ms.date: 11/04/2016
f1_keywords:
- tuple_size
- std::tuple_size
- utility/std::tuple_size
helpviewer_keywords:
- std::tuple_size
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
ms.openlocfilehash: e825acc02e27a8d0c1ae29e5bfcf4ac1e0a708b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168880"
---
# <a name="tuple_size-class"></a>tuple_size 클래스

`tuple` 에 포함된 요소 수를 보관합니다.

## <a name="syntax"></a>구문

```cpp
// TEMPLATE STRUCT tuple_size
template <class Tuple>
   struct tuple_size;

// number of elements in array
template <class Elem, size_t Size>
   struct tuple_size<array<Elem, Size>>
      : integral_constant<size_t, Size>;

// size of pair
template <class T1, class T2>
   struct tuple_size<pair<T1, T2>>
      : integral_constant<size_t, 2>

// size of tuple
template <class... Types>
   struct tuple_size<tuple<Types...>>
      : integral_constant<size_t, sizeof...(Types)>;

// size of const tuple
template <class Tuple>
   struct tuple_size<const Tuple>;

// size of volatile tuple
template <class Tuple>
   struct tuple_size<volatile Tuple>;

// size of const volatile tuple
template <class Tuple>
   struct tuple_size<const volatile Tuple>;
```

```cpp
template <class T> inline constexpr size_t tuple_size_v = tuple_size<T>::value;
```

### <a name="parameters"></a>매개 변수

*튜플이*\
튜플의 형식입니다.

*E*\
배열 요소의 형식입니다.

*크기가*\
배열의 크기입니다.

*들은*\
쌍의 첫 번째 구성원 형식입니다.

*T*\
쌍의 두 번째 구성원 형식입니다.

*종류*\
튜플 요소의 형식입니다.

## <a name="remarks"></a>설명

클래스 템플릿에는 `value` 값이 튜플 형식 *튜플의* 범위를 갖는 정수 계열 상수 식인 멤버가 있습니다.

배열의 템플릿 특수화에는 해당 `value` 값이 배열의 크기인 정수 계열 상수 식인 멤버가 있습니다. 

쌍의 템플릿 특수화에는 해당 값이 2인 정수 계열 상수 식 `value` 구성원이 있습니다.

## <a name="example"></a>예제

```cpp
#include <tuple>
#include <iostream>

using namespace std;

typedef tuple<int, double, int, double> MyTuple;
int main()
{
    MyTuple c0(0, 1.5, 2, 3.7);

    // display contents "0 1 2 3"
    cout << get<0>(c0);
    cout << " " << get<1>(c0);
    cout << " " << get<2>(c0);
    cout << " " << get<3>(c0) << endl;

    // display size "4"
    cout << " " << tuple_size<MyTuple>::value << endl;
}
```

```Output
0 1.5 2 3.7
4
```

## <a name="requirements"></a>요구 사항

**헤더:**\<tuple>

**헤더:** \<array> (배열 특수화의 경우)

**헤더:** \<utility> (쌍 특수화의 경우)

**네임스페이스:** std
