---
title: logical_and 구조체
ms.date: 11/04/2016
f1_keywords:
- functional/std::logical_and
helpviewer_keywords:
- logical_and class
- logical_and struct
ms.assetid: 1a375cc2-0592-4d57-a553-78009c7ad610
ms.openlocfilehash: cc75c93d5173ceb7fa12b9722a797499b4225a53
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821618"
---
# <a name="logical_and-struct"></a>logical_and 구조체

인수에서 논리적 결합 작업 (`operator&&`)을 수행 하는 미리 정의 된 함수 개체입니다.

## <a name="syntax"></a>구문

```
template <class Type = void>
struct logical_and : public binary_function<Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator&&
template <>
struct logical_and<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) && std::forward<U>(Right));
};
```

### <a name="parameters"></a>매개 변수

*형식*, *T*, *U*\
지정되었거나 유추된 형식의 피연산자를 가져오는 `operator&&`를 지원하는 모든 형식입니다.

*Left*\
논리곱 연산의 왼쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue*참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *T*의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

*Right*\
논리곱 연산의 오른쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue*참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *U*의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

## <a name="return-value"></a>반환 값

`Left && Right`의 결과입니다. 특수화된 템플릿은 `operator&&`에 의해 반환되는 형식을 가지고 있는 결과를 완벽하게 전달합니다.

## <a name="remarks"></a>주의

사용자 정의 형식의 경우 피연산자 평가의 단락(short-circuiting)이 없습니다. 두 인수 모두 `operator&&`로 평가됩니다.

## <a name="example"></a>예

```cpp
// functional_logical_and.cpp
// compile with: /EHsc

#define _CRT_RAND_S
#include <stdlib.h>
#include <deque>
#include <algorithm>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   deque<bool> d1, d2, d3( 7 );
   deque<bool>::iterator iter1, iter2, iter3;

   unsigned int randomValue;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
   {
      if ( rand_s( &randomValue ) == 0 )
      {
         d1.push_back((bool)(( randomValue % 2 ) != 0));
      }

   }

   int j;
   for ( j = 0 ; j < 7 ; j++ )
   {
      if ( rand_s( &randomValue ) == 0 )
      {
         d2.push_back((bool)(( randomValue % 2 ) != 0));
      }
   }

   cout << boolalpha;    // boolalpha I/O flag on

   cout << "Original deque:\n d1 = ( " ;
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )
      cout << *iter1 << " ";
   cout << ")" << endl;

   cout << "Original deque:\n d2 = ( " ;
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )
      cout << *iter2 << " ";
   cout << ")" << endl;

   // To find element-wise conjunction of the truth values
   // of d1 & d2, use the logical_and function object
   transform( d1.begin( ), d1.end( ), d2.begin( ),
      d3.begin( ), logical_and<bool>( ) );
   cout << "The deque which is the conjunction of d1 & d2 is:\n d3 = ( " ;
   for ( iter3 = d3.begin( ) ; iter3 != d3.end( ) ; iter3++ )
      cout << *iter3 << " ";
   cout << ")" << endl;
}
```

```Output
Original deque:
d1 = ( true true true true true false false )
Original deque:
d2 = ( true false true true false true false )
The deque which is the conjunction of d1 & d2 is:
d3 = ( true false true true false false false )
```
