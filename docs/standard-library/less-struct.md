---
description: '자세히 알아보기: less 구조체'
title: less 구조체
ms.date: 11/04/2016
f1_keywords:
- functional/std::less
helpviewer_keywords:
- less struct
- less function
ms.assetid: 39349da3-11cd-4774-b2cc-b46af5aae5d7
ms.openlocfilehash: b80789f2d2f2c8d1267450a39c39317af1da9244
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312880"
---
# <a name="less-struct"></a>less 구조체

인수에서 보다 작음 연산 ()을 수행 하는 이진 조건자입니다 `operator<` .

## <a name="syntax"></a>구문

```cpp
template <class Type = void>
struct less : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<
template <>
struct less<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) <std::forward<U>(Right));
};
```

### <a name="parameters"></a>매개 변수

*형식*, *T*, *U*\
지정되었거나 유추된 형식의 피연산자를 가져오는 `operator<`를 지원하는 모든 형식입니다.

*비어*\
작음 연산의 왼쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *T* 의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

*오른쪽*\
작음 연산의 오른쪽 피연산자입니다. 특수화 되지 않은 *템플릿은 형식의 lvalue* 참조 인수를 사용 합니다. 특수화 된 템플릿은 유추 형식 *U* 의 lvalue 및 rvalue 참조 인수를 완벽 하 게 전달 합니다.

## <a name="return-value"></a>반환 값

`Left < Right`의 결과입니다. 특수화된 템플릿은 `operator<`에 의해 반환되는 형식을 가지고 있는 결과를 완벽하게 전달합니다.

## <a name="remarks"></a>설명

`less` < `Type` 이 형식이 정렬 되기 위한 표준 수학적 요구 사항을 충족 하는 경우에만 이진 조건자> *형식 형식의* 요소 값 집합을 동등 클래스에 대 한 엄격한 약한 순서로 제공 합니다. 고유한 값의 모든 요소가 서로를 기준으로 정렬된다는 점에서 모든 포인터 형식에 대한 특수화는 요소의 전체 순서 지정을 생성합니다.

## <a name="example"></a>예제

```cpp
// functional_less.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

struct MyStruct {
   MyStruct(int i) : m_i(i){}

   bool operator < (const MyStruct & rhs) const {
      return m_i < rhs.m_i;
   }

   int m_i;
};

int main() {
   using namespace std;
   vector <MyStruct> v1;
   vector <MyStruct>::iterator Iter1;
   vector <MyStruct>::reverse_iterator rIter1;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
       v1.push_back( MyStruct(rand()));

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )
cout << Iter1->m_i << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   sort( v1.begin( ), v1.end( ), less<MyStruct>());

   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )
cout << Iter1->m_i << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (41 18467 6334 26500 19169 15724 11478)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500)
```
