---
description: '다음에 대 한 자세한 정보: gslice 클래스'
title: gslice 클래스
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice
- valarray/std::gslice::size
- valarray/std::gslice::start
- valarray/std::gslice::stride
helpviewer_keywords:
- std::gslice [C++]
- std::gslice [C++], size
- std::gslice [C++], start
- std::gslice [C++], stride
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
ms.openlocfilehash: 92bb8d56df40a7d59c5414aca3e0d5846401e805
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324150"
---
# <a name="gslice-class"></a>gslice 클래스

valarray의 다차원 하위 집합을 정의하는 데 사용되는 valarray에 대한 유틸리티 클래스입니다. valarray가 배열의 모든 요소를 포함하는 다차원 행렬로 간주되는 경우 조각은 다차원 배열에서 벡터를 추출합니다.

## <a name="remarks"></a>설명

클래스는 [gslice_array](../standard-library/gslice-array-class.md) 형식의 개체 특징을 결정하는 매개 변수를 저장합니다. Gslice 클래스의 개체가 [valarray](../standard-library/valarray-class.md#op_at)클래스의 개체에 대 한 인수로 표시 되는 경우 valarray의 하위 집합이 간접적으로 생성 됩니다 **\<Type>** . 부모 valarray에서 선택되는 하위 집합을 지정하는 저장된 값은 다음과 같습니다.

- 시작 인덱스

- 클래스의 길이 벡터 `valarray<size_t>` 입니다.

- 클래스의 stride 벡터 `valarray<size_t>` 입니다.

두 벡터는 길이가 같아야 합니다.

gslice에서 정의된 집합이 상수 valarray의 하위 집합인 경우 gslice은 새 valarray입니다. gslice에서 정의된 집합이 비상수 valarray의 하위 집합인 경우 gslice에 원래 valarray에 대한 참조 의미 체계가 있습니다. 비상수 valarray에 대한 평가 메커니즘은 시간과 메모리를 절약합니다.

gslice에서 정의된 소스 및 대상 하위 집합이 고유하고 모든 인덱스가 유효한 경우에만 valarray에 대한 작업이 보장됩니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[gslice](#gslice)|모두 지정된 요소에서 시작하는 `valarray`의 여러 조각으로 구성된 `valarray`의 하위 집합을 정의합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[size](#size)|`valarray`의 일반 조각 요소 수를 지정하는 배열 값을 찾습니다.|
|[start](#start)|`valarray`의 일반 조각 시작 인덱스를 찾습니다.|
|[스트라이드](#stride)|`valarray`의 일반 조각 요소 간의 거리를 찾습니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<valarray>

**네임스페이스:** std

## <a name="gslicegslice"></a><a name="gslice"></a> gslice:: gslice

valarray의 다차원 조각을 정의하는 데 사용되는 valarray에 대한 유틸리티 클래스입니다.

```cpp
gslice();

gslice(
    size_t _StartIndex,
    const valarray<size_t>& _LenArray,
    const valarray<size_t>& _IncArray);
```

### <a name="parameters"></a>매개 변수

*_StartIndex*\
하위 집합에 있는 첫 번째 요소의 valarray 인덱스입니다.

*_LenArray*\
각 조각의 요소 수를 지정하는 배열입니다.

*_IncArray*\
각 조각에서 진행 속도를 지정하는 배열입니다.

### <a name="return-value"></a>반환 값

기본 생성자는 시작 인덱스에 대해 0을 저장하고 길이 및 진행 속도 벡터에 대해 0 길이 벡터를 저장합니다. 두 번째 생성자는 시작 인덱스, 길이 배열의 *_LenArray* , stride 배열의 *_IncArray* 에 대 한 *_StartIndex* 를 저장 합니다.

### <a name="remarks"></a>설명

**gslice** 는 각각 동일한 지정된 요소에서 시작되는 valarray의 여러 조각으로 구성된 valarray 하위 집합을 정의합니다. 배열을 사용하여 여러 조각을 정의하는 기능은 `gslice`와 [slice::slice](../standard-library/slice-class.md#slice) 간의 유일한 차이점입니다. 첫 번째 조각에는 *_StartIndex* 인덱스를 사용 하는 첫 번째 요소, *_LenArray* 의 첫 번째 요소에 의해 지정 된 요소 수 및 *_IncArray* 의 첫 번째 요소에서 제공 하는 스트라이드가 있습니다. 직교 조각의 다음 set에는 첫 번째 조각이 제공한 첫 번째 요소가 있습니다. *_LenArray* 의 두 번째 요소는 요소 수를 지정 합니다. Stride는 *_IncArray* 의 두 번째 요소에 의해 제공 됩니다. 조각의 세 번째 차원은 2차원 배열의 요소를 시작 요소로 사용하고 비슷하게 진행됩니다.

### <a name="example"></a>예제

```cpp
// gslice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:" << endl << "(";
   for ( i = 0 ; i < 20 ; i++ )
      cout << " " << va [ i ];
   cout << " )" << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];

   cout << "The valarray for vaGSlice is vaResult:" << endl
        << "va[vaGSlice] = (";

   for ( i = 0 ; i < 8 ; i++ )
      cout << " " << vaResult [ i ];
   cout << ")" << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 )
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19)
```

## <a name="gslicesize"></a><a name="size"></a> gslice:: size

valarray의 일반 조각 요소 수를 지정하는 배열 값을 찾습니다.

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>반환 값

valarray의 일반 조각 중 각 조각의 요소 수를 지정하는 valarray입니다.

### <a name="remarks"></a>설명

멤버 함수는 저장된 조각 길이를 반환합니다.

### <a name="example"></a>예제

```cpp
// gslice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> sizeGS = vaGSlice.size ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The size of vaResult is:"
        << "\n vaGSlice.size ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << sizeGS[ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The size of the valarray is: 20.

The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The size of vaResult is:
vaGSlice.size ( ) = ( 4 4 ).
```

## <a name="gslicestart"></a><a name="start"></a> gslice:: start

valarray의 일반 조각 시작 인덱스를 찾습니다.

```cpp
size_t start() const;
```

### <a name="return-value"></a>반환 값

valarray의 일반 조각 시작 인덱스입니다.

### <a name="example"></a>예제

```cpp
// gslice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   size_t vaGSstart = vaGSlice.start ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The index of the first element of vaResult is: "
        << vaGSstart << "." << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The index of the first element of vaResult is: 0.
```

## <a name="gslicestride"></a><a name="stride"></a> gslice:: stride

valarray의 일반 조각 요소 간의 거리를 찾습니다.

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>반환 값

valarray의 일반 조각 중 각 조각의 요소 간 거리를 지정하는 valarray입니다.

### <a name="example"></a>예제

```cpp
// gslice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for (i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> strideGS = vaGSlice.stride ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The strides of vaResult are:"
        << "\n vaGSlice.stride ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << strideGS[ i ] << " ";
   cout << ")." << endl;

}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The strides of vaResult are:
vaGSlice.stride ( ) = ( 7 4 ).
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
