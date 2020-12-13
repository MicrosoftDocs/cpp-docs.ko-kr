---
description: Mask_array 클래스에 대해 자세히 알아보세요.
title: mask_array 클래스
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: d3eb105c7779ff54ddbec3d68a518dc74d089903
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149359"
---
# <a name="mask_array-class"></a>mask_array 클래스

하위 집합 배열 간의 작업을 제공 하 여 부울 식으로 지정 되는 부모 valarrays의 하위 집합인 개체를 지 원하는 내부 보조 클래스 템플릿입니다.

## <a name="syntax"></a>구문

## <a name="remarks"></a>설명

이 클래스는 `va` [](../standard-library/valarray-class.md) **\<Type>** `ba` 개체에서 선택할 요소의 시퀀스를 설명 하는 [ \<bool> valarray](../standard-library/valarray-bool-class.md)클래스의 개체와 함께 valarray 클래스의 개체에 대 한 참조를 저장 하는 개체를 설명 합니다 `valarray<Type>` .

`mask_array<Type>` [Va&#91;ba&#93;](../standard-library/valarray-class.md#op_at)형식의 식을 작성 하 여 개체를 생성 합니다. 그런 다음 클래스 mask_array의 멤버 함수는 `valarray<Type>` 선택한 요소의 시퀀스에만 영향을 주는 점을 제외 하 고에 대해 정의 된 해당 함수 서명 처럼 동작 합니다.

시퀀스는 대부분의 요소로 구성 됩니다 `ba.size` . 요소 *J* 는 **ba**[ *J*]가 true 인 경우에만 포함 됩니다. 따라서에 참인 요소가 있으므로 시퀀스에 요소가 많이 있습니다 `ba` . `I`이에서 가장 낮은 true 요소의 인덱스인 경우 `ba` **va**[ `I` ]는 선택한 시퀀스의 요소 0입니다.

## <a name="example"></a>예제

```cpp
// mask_array.cpp
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

   // Use masked subsets to assign a value of 10
   // to all elements grrater than 3 in value
   va [va > 3 ] = 10;
   cout << "The modified operand valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
```

### <a name="output"></a>출력

```Output
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).
```

## <a name="requirements"></a>요구 사항

**헤더:**\<valarray>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
