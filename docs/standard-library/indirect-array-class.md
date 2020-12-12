---
description: Indirect_array 클래스에 대해 자세히 알아보세요.
title: indirect_array 클래스
ms.date: 11/04/2016
f1_keywords:
- valarray/std::indirect_array
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
ms.openlocfilehash: 47c9a0e604fd9873d7705f70624e67d9b3a22a7a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324043"
---
# <a name="indirect_array-class"></a>indirect_array 클래스

부모 valarray의 인덱스 하위 집합을 지정 하 여 정의 된 하위 집합 배열 간의 작업을 제공 하 여 valarray의 하위 집합인 개체를 지 원하는 내부 보조 클래스 템플릿입니다.

## <a name="syntax"></a>구문

## <a name="remarks"></a>설명

이 클래스는 `va` [](../standard-library/valarray-class.md) **\<Type>** `xa` `valarray<size_t>` 개체에서 선택할 요소의 시퀀스를 설명 하는 클래스의 개체와 함께 valarray 클래스의 개체에 대 한 참조를 저장 하는 개체를 설명 합니다 `valarray<Type>` .

`indirect_array<Type>`폼의 식을 작성 하 여 개체를 생성 `va[xa]` 합니다. 그런 다음 클래스 indirect_array의 멤버 함수는 `valarray<Type>` 선택한 요소의 시퀀스에만 영향을 주는 점을 제외 하 고에 대해 정의 된 해당 함수 서명 처럼 동작 합니다.

이 시퀀스는 xa로 구성 됩니다 **.** 요소의 [크기를 조정](../standard-library/valarray-class.md#size) 합니다. 여기서 요소는의 `I` 인덱스 **xa**[]가 됩니다 `I` `va` .

## <a name="example"></a>예제:

```cpp
// indirect_array.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      va [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 2 )
      va [ i ] =  -1;

   cout << "The initial operand valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   // Select 2nd, 4th & 6th elements
   // and assign a value of 10 to them
   valarray<size_t> indx ( 3 );
   indx [0] = 2;
   indx [1] = 4;
   indx [2] = 6;
   va[indx] = 10;

   cout << "The modified operand valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
```

### <a name="output"></a>출력

```cpp
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).
```

## <a name="requirements"></a>요구 사항

**헤더:**\<valarray>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
