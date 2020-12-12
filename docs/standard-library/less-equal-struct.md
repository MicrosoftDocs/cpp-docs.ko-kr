---
description: '다음에 대 한 자세한 정보: less_equal 구조체'
title: less_equal 구조체
ms.date: 11/04/2016
f1_keywords:
- functional/std::less_equal
helpviewer_keywords:
- less_equal function
- less_equal struct
ms.assetid: 32085782-c7e0-4310-9b40-8aa3c1bff211
ms.openlocfilehash: b2d715971c5278629a6ea812c5a9c199f00c4a07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312893"
---
# <a name="less_equal-struct"></a>less_equal 구조체

인수에서 작거나 같음 연산 ()을 수행 하는 이진 조건자입니다 `operator<=` .

## <a name="syntax"></a>구문

```cpp
template <class Type = void>
struct less_equal : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<=
template <>
struct less_equal<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    -> decltype(std::forward<T>(Left) <= std::forward<U>(Right));
};
```

### <a name="parameters"></a>매개 변수

*형식*, *T*, *U*\
지정되었거나 유추된 형식의 피연산자를 가져오는 `operator<=`를 지원하는 모든 형식입니다.

*비어*\
작거나 같음 연산의 왼쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *T* 의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

*오른쪽*\
작거나 같음 연산의 오른쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *U* 의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

## <a name="return-value"></a>반환 값

`Left <= Right`의 결과입니다. 특수 템플릿은 `operator<=`에 의해 반환되는 형식을 포함하는 결과를 완벽하게 전달합니다.

## <a name="remarks"></a>설명

`less_equal` < `Type` 이 형식이 정렬 되기 위한 표준 수학적 요구 사항을 충족 하는 경우에만 이진 조건자> *형식 형식의* 요소 값 집합을 동등 클래스에 대 한 엄격한 약한 순서로 제공 합니다. 고유한 값의 모든 요소가 서로를 기준으로 정렬된다는 점에서 모든 포인터 형식에 대한 특수화는 요소의 전체 순서 지정을 생성합니다.

## <a name="example"></a>예제

```cpp
// functional_less_equal.cpp
// compile with: /EHsc
#define _CRT_RAND_S
#include <stdlib.h>
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
   vector <int>::reverse_iterator rIter1;
   unsigned int randomNumber;

   int i;
   for ( i = 0 ; i < 5 ; i++ )
   {
      if ( rand_s( &randomNumber ) == 0 )
      {
         // Convert the random number to be between 1 - 50000
         // This is done for readability purposes
         randomNumber = ( unsigned int) ((double)randomNumber /
            (double) UINT_MAX * 50000) + 1;

         v1.push_back( randomNumber );
      }
   }
   for ( i = 0 ; i < 3 ; i++ )
   {
      v1.push_back( 2836 );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use the binary predicate less_equal<int>( )
   sort( v1.begin( ), v1.end( ), less_equal<int>( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (31247 37154 48755 15251 6205 2836 2836 2836)
Sorted vector v1 = (2836 2836 2836 6205 15251 31247 37154 48755)
```
