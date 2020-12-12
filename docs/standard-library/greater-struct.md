---
description: '자세히 알아보기: 더 큰 구조체'
title: greater 구조체
ms.date: 11/04/2016
f1_keywords:
- functional/std::greater
helpviewer_keywords:
- greater struct
- greater function
ms.assetid: ebc348e1-edcd-466b-b21a-db95bd8f9079
ms.openlocfilehash: fabee76d20d201f63b9f5397c20409ad62125657
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324176"
---
# <a name="greater-struct"></a>greater 구조체

인수에 대해 보다 큼 연산 ()을 수행 하는 이진 조건자입니다 `operator>` .

## <a name="syntax"></a>구문

```cpp
template <class Type = void>
struct greater : public binary_function <Type, Type, bool>
{
    bool operator()(
    const Type& Left,
    const Type& Right) const;

};

// specialized transparent functor for operator>
template <>
struct greater<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    ->  decltype(std::forward<T>(Left)> std::forward<U>(Right));
};
```

### <a name="parameters"></a>매개 변수

*형식*, *T*, *U*\
지정되었거나 유추된 형식의 피연산자를 가져오는 `operator>`를 지원하는 모든 형식입니다.

*비어*\
큼 연산의 왼쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *T* 의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

*오른쪽*\
큼 연산의 오른쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *U* 의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

## <a name="return-value"></a>반환 값

`Left > Right`의 결과입니다. 특수화된 템플릿은 `operator>`에 의해 반환되는 형식을 가지고 있는 결과를 완벽하게 전달합니다.

## <a name="remarks"></a>설명

`greater` < `Type` 이 형식이 정렬 되기 위한 표준 수학적 요구 사항을 충족 하는 경우에만 이진 조건자> *형식 형식의* 요소 값 집합을 동등 클래스에 대 한 엄격한 약한 순서로 제공 합니다. 고유한 값의 모든 요소가 서로를 기준으로 정렬된다는 점에서 모든 포인터 형식에 대한 특수화는 요소의 전체 순서 지정을 생성합니다.

## <a name="example"></a>예제

```cpp
// functional_greater.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i < 8 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // specify binary predicate greater<int>( )
   sort( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (41 18467 6334 26500 19169 15724 11478 29358)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500 29358)
Resorted vector v1 = (29358 26500 19169 18467 15724 11478 6334 41)
```
