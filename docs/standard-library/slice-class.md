---
description: '자세히 알아보기: slice 클래스'
title: slice 클래스
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice
- valarray/std::slice::size
- valarray/std::slice::start
- valarray/std::slice::stride
helpviewer_keywords:
- std::slice [C++]
- std::slice [C++], size
- std::slice [C++], start
- std::slice [C++], stride
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
ms.openlocfilehash: a2a738db5bf3479c58e6b4ddd4d29a3a7ba84b23
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153904"
---
# <a name="slice-class"></a>slice 클래스

부모 valarray의 1차원 하위 집합을 정의하는 데 사용되는 valarray에 대한 유틸리티 클래스입니다. valarray가 배열의 모든 요소를 포함하는 2차원 행렬로 간주되는 경우 조각은 2차원 배열에서 1차원 벡터를 추출합니다.

## <a name="remarks"></a>설명

클래스는 클래스 조각의 개체가 [valarray](../standard-library/valarray-class.md#op_at)클래스의 개체에 대 한 인수로 나타날 때 valarray의 하위 집합이 간접적으로 생성 되 [slice_array](../standard-library/slice-array-class.md) 형식 개체의 특징을 나타내는 매개 변수를 저장 합니다 **\<Type>** . 부모 valarray에서 선택되는 하위 집합을 지정하는 저장된 값은 다음과 같습니다.

- 배열의 시작 인덱스입니다.

- 조각의 총 길이 또는 요소 수입니다.

- valarray에서 이후 요소 인덱스 사이의 거리 또는 진행 속도입니다.

slice에서 정의된 집합이 상수 valarray의 하위 집합인 경우 slice는 새 valarray입니다. slice에서 정의된 집합이 비상수 valarray의 하위 집합인 경우 slice에 원래 valarray에 대한 참조 의미 체계가 있습니다. 비상수 valarray에 대한 평가 메커니즘은 시간과 메모리를 절약합니다.

slice에서 정의된 소스 및 대상 하위 집합이 고유하고 모든 인덱스가 유효한 경우에만 valarray에 대한 작업이 보장됩니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[조각](#slice)|동일한 거리만큼 떨어져 있고 지정된 요소에서 시작하는 많은 요소로 구성된 `valarray`의 하위 집합을 정의합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[size](#size)|`valarray`의 조각에 있는 요소 수를 찾습니다.|
|[start](#start)|`valarray`의 조각 시작 인덱스를 찾습니다.|
|[스트라이드](#stride)|`valarray`의 조각 요소 간의 거리를 찾습니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<valarray>

**네임스페이스:** std

## <a name="slicesize"></a><a name="size"></a> slice:: size

valarray의 조각에 있는 요소 수를 찾습니다.

```cpp
size_t size() const;
```

### <a name="return-value"></a>반환 값

valarray의 조각에 있는 요소의 수입니다.

### <a name="example"></a>예제

```cpp
// slice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA, sizeVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   sizeVAR = vaSlice.size ( );
   cout << "The size of slice vaSlice is: "
        << sizeVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The size of the valarray is: 20.

The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The size of slice vaSlice is: 6.
```

## <a name="sliceslice"></a><a name="slice"></a> slice:: slice

동일한 거리만큼 떨어져 있고 지정된 요소에서 시작하는 많은 요소로 구성된 valarray의 하위 집합을 정의합니다.

```cpp
slice();

slice(
    size_t _StartIndex,
    size_t _Len,
    size_t stride);
```

### <a name="parameters"></a>매개 변수

*_StartIndex*\
하위 집합에 있는 첫 번째 요소의 valarray 인덱스입니다.

*_Len*\
하위 집합의 요소 수입니다.

*스트라이드*\
하위 집합의 요소 간 거리입니다.

### <a name="return-value"></a>반환 값

기본 생성자는 시작 인덱스, 총 길이 및 진행 속도에 대해 0을 저장합니다. 두 번째 생성자는 시작 인덱스에 대 한 *_StartIndex* 를 저장 하 고, 전체 길이를 *_Len* 하 고, stride에 대해 *stride* 를 저장 합니다.

### <a name="remarks"></a>설명

진행 속도는 음수일 수 있습니다.

### <a name="example"></a>예제

```cpp
// slice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  2 * (i + 1 );

   cout << "The operand valarray va is:\n( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 1 , 7 , 3 );
   vaResult = va [ vaSlice ];

   cout << "\nThe slice of valarray va is vaResult:"
        << "\nva[slice( 1, 7, 3)] = ( ";
      for ( i = 0 ; i < 7 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
( 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 ).

The slice of valarray va is vaResult:
va[slice( 1, 7, 3)] = ( 4 10 16 22 28 34 40 ).
```

## <a name="slicestart"></a><a name="start"></a> slice:: start

valarray 조각의 시작 인덱스를 찾습니다.

```cpp
size_t start() const;
```

### <a name="return-value"></a>반환 값

valarray 조각의 시작 인덱스입니다.

### <a name="example"></a>예제

```cpp
// slice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t startVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] = i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   startVAR = vaSlice.start ( );
   cout << "The start index of slice vaSlice is: "
        << startVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The start index of slice vaSlice is: 3.
```

## <a name="slicestride"></a><a name="stride"></a> slice:: stride

valarray의 조각 내 요소 간 거리를 찾습니다.

```cpp
size_t stride() const;
```

### <a name="return-value"></a>반환 값

valarray의 조각 내 요소 간 거리입니다.

### <a name="example"></a>예제

```cpp
// slice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t strideVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  3 * ( i + 1 );

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 4 , 5 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 4, 5, 3)] =\n ( ";
      for ( i = 0 ; i < 5 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   strideVAR = vaSlice.stride ( );
   cout << "The stride of slice vaSlice is: "
        << strideVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45 48 51 54 57 60 ).
The slice of valarray va is vaResult = va[slice( 4, 5, 3)] =
( 15 24 33 42 51 ).
The stride of slice vaSlice is: 3.
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
