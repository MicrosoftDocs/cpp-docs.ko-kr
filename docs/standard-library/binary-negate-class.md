---
description: Binary_negate 클래스에 대해 자세히 알아보세요.
title: binary_negate 클래스
ms.date: 02/21/2019
f1_keywords:
- functional/std::binary_negate
helpviewer_keywords:
- binary_negate class
ms.assetid: 7b86f02c-af7e-4c7f-9df1-08addae4dd65
ms.openlocfilehash: f97b1ec31623ece91c76b1195c87f75e8cdfd2eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325534"
---
# <a name="binary_negate-class"></a>binary_negate 클래스

지정 된 이항 함수의 반환 값을 부정 하는 멤버 함수를 제공 하는 클래스 템플릿입니다. C + + 17에서 더 이상 사용 되지 않는 [not_fn](functional-functions.md#not_fn)입니다.

## <a name="syntax"></a>구문

```cpp
template <class Operation>
class binary_negate
    : public binaryFunction <typename Operation::first_argument_type,
                              typename Operation::second_argument_type, bool>
{
    explicit binary_negate(const Operation& Func);
    bool operator()(const typename Operation::first_argument_type& left,
                    const typename Operation::second_argument_type& right) const;
};
```

### <a name="parameters"></a>매개 변수

*Func*\
부정할 이항 함수입니다.

*비어*\
부정할 이항 함수의 왼쪽 피연산자입니다.

*오른쪽*\
부정할 이항 함수의 오른쪽 피연산자입니다.

## <a name="return-value"></a>반환 값

이항 함수의 부정입니다.

## <a name="remarks"></a>설명

클래스 템플릿은 이진 함수 개체 *Func* 의 복사본을 저장 합니다. 반환 하는 멤버 함수 `operator()` 를 정의 `!Func(left, right)` 합니다.

`binary_negate`의 생성자는 직접 사용되는 경우가 거의 없습니다. **binary_negator** 어댑터 조건자를 선언하고 사용하는 데 일반적으로 [not2](../standard-library/functional-functions.md#not2) 도우미 함수가 사용됩니다.

## <a name="example"></a>예제

```cpp
// functional_binary_negate.cpp
// compile with: /EHsc
#define _CRT_RAND_S
#include <stdlib.h>

#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   vector <unsigned int> v1;
   vector <unsigned int>::iterator Iter1;

   unsigned int i;
   v1.push_back( 6262 );
   v1.push_back( 6262 );
   unsigned int randVal = 0;
   for ( i = 0 ; i < 5 ; i++ )
   {
      rand_s(&randVal);
      v1.push_back( randVal );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<unsigned int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // use the binary_negate function
   sort( v1.begin( ), v1.end( ),
   binary_negate<less<unsigned int> >(less<unsigned int>( ) ) );

   // The helper function not2 could also have been used
   // in the above line and is usually preferred for convenience
   // sort( v1.begin( ), v1.end( ), not2(less<unsigned int>( ) ) );

   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 6262 6262 2233879413 2621500314 580942933 3715465425 3739828298 )
Sorted vector v1 = ( 6262 6262 580942933 2233879413 2621500314 3715465425 3739828298 )
Resorted vector v1 = ( 3739828298 3715465425 2621500314 2233879413 580942933 6262 6262 )
```
