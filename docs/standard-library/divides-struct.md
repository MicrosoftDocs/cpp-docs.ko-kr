---
title: divides 구조체
ms.date: 11/04/2016
f1_keywords:
- functional/std::divides
helpviewer_keywords:
- divides struct
- divides class
ms.assetid: b9cf8e9c-6981-43a6-a6a3-8f761987dd7a
ms.openlocfilehash: 6c7297fa7c31470591b473ab5eadcde54e8c3b34
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244142"
---
# <a name="divides-struct"></a>divides 구조체

나누기 연산을 수행 하는 미리 정의 된 함수 개체 (`operator/`) 인수에 대해 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Type = void>
struct divides : public binary_function <Type, Type, Type>
{
    Type operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator/
template <>
struct divides<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    -> decltype(std::forward<T>(Left)*/ std::forward<U>(Right));
};
```

### <a name="parameters"></a>매개 변수

*형식*하십시오 *T*, *U*\
지정되었거나 유추된 형식의 피연산자를 가져오는 `operator/`를 지원하는 형식입니다.

*왼쪽*\
나누기 연산의 왼쪽 피연산자입니다. 형식의 lvalue 참조 인수를 사용 하는 특수화 되지 않은 템플릿은 *형식*합니다. 특수화 된 템플릿은 완벽 하 게 전달의 lvalue 및 rvalue 참조 인수 형식 유추 *T*합니다.

*오른쪽*\
나누기 연산의 오른쪽 피연산자입니다. 형식의 lvalue 참조 인수를 사용 하는 특수화 되지 않은 템플릿은 *형식*합니다. 특수화 된 템플릿은 완벽 하 게 전달의 lvalue 및 rvalue 참조 인수 형식 유추 *U*합니다.

## <a name="return-value"></a>반환 값

`Left / Right`의 결과입니다. 특수화된 템플릿은 `operator/`에 의해 반환되는 형식을 가지고 있는 결과를 완벽하게 전달합니다.

## <a name="example"></a>예제

```cpp
// functional_divides.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main( )
{
   vector <double> v1, v2, v3 (6);
   vector <double>::iterator Iter1, Iter2, Iter3;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 7.0 * i );
   }

   int j;
   for ( j = 1 ; j <= 6 ; j++ )
   {
      v2.push_back( 2.0 * j);
   }

   cout << "The vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "The vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Finding the element-wise quotients of the elements of v1 & v2
   transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin ( ),
      divides<double>( ) );

   cout << "The element-wise quotients are: ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
```

```Output
The vector v1 = ( 0 7 14 21 28 35 )
The vector v2 = ( 2 4 6 8 10 12 )
The element-wise quotients are: ( 0 1.75 2.33333 2.625 2.8 2.91667 )
```
