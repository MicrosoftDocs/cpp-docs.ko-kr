---
description: Reinterpret_cast 연산자에 대해 자세히 알아보세요.
title: reinterpret_cast 연산자
ms.date: 11/04/2016
f1_keywords:
- reinterpret_cast_cpp
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
ms.openlocfilehash: 71b7067321c5af1e81311f7ce036c735c96193d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252443"
---
# <a name="reinterpret_cast-operator"></a>reinterpret_cast 연산자

포인터가 다른 포인터 형식으로 변환될 수 있도록 합니다. 또한 정수 계열 형식이 포인터 형식으로 변환될 수 있도록 하고 그 반대로도 변환될 수 있도록 합니다.

## <a name="syntax"></a>구문

```
reinterpret_cast < type-id > ( expression )
```

## <a name="remarks"></a>설명

연산자의 오용은 **`reinterpret_cast`** 안전 하지 않을 수 있습니다. 원하는 변환이 본질적으로 낮은 수준이 아닌 한 다른 캐스트 연산자 중 하나를 사용해야 합니다.

연산자는 기본적으로 **`reinterpret_cast`** **`char*`** **`int*`** `One_class*` 안전 하지 않은 (예:) 또는로의 변환에 사용할 수 있습니다 `Unrelated_class*` .

의 결과는 **`reinterpret_cast`** 원래 형식으로 다시 캐스팅 되는 것 외에는 안전 하 게 사용할 수 없습니다. 다른 용도로 사용하는 경우에는 기껏해야 이식할 수 없는 결과가 생성됩니다.

**`reinterpret_cast`** 연산자는 **`const`** , **`volatile`** 또는 특성으로 캐스트할 수 없습니다 **`__unaligned`** . 이러한 특성을 제거 하는 방법에 대 한 자세한 내용은 [Const_cast 연산자](../cpp/const-cast-operator.md) 를 참조 하세요.

**`reinterpret_cast`** 연산자는 null 포인터 값을 대상 형식의 null 포인터 값으로 변환 합니다.

는 **`reinterpret_cast`** 해시 함수에 있습니다 .이 함수는 두 개의 고유 값이 동일한 인덱스로 끝나지 않는 방식으로 값을 인덱스에 매핑합니다.

```cpp
#include <iostream>
using namespace std;

// Returns a hash code based on an address
unsigned short Hash( void *p ) {
   unsigned int val = reinterpret_cast<unsigned int>( p );
   return ( unsigned short )( val ^ (val >> 16));
}

using namespace std;
int main() {
   int a[20];
   for ( int i = 0; i < 20; i++ )
      cout << Hash( a + i ) << endl;
}

Output:
64641
64645
64889
64893
64881
64885
64873
64877
64865
64869
64857
64861
64849
64853
64841
64845
64833
64837
64825
64829
```

를 **`reinterpret_cast`** 사용 하면 포인터를 정수 계열 형식으로 처리할 수 있습니다. 결과는 비트 이동되고 자신과 XOR 연산이 수행되어 고유한 인덱스(높은 확률로 고유함)를 생성합니다. 이 인덱스는 표준 C 스타일 캐스트를 통해 함수의 반환 형식으로 잘립니다.

## <a name="see-also"></a>참고 항목

[캐스팅 연산자](../cpp/casting-operators.md)<br/>
[키워드](../cpp/keywords-cpp.md)
