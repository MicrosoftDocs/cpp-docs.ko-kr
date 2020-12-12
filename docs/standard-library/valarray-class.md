---
description: 다음에 대해 자세히 알아보세요. valarray 클래스
title: valarray 클래스
ms.date: 03/27/2019
f1_keywords:
- valarray/std::valarray
- valarray/std::valarray::value_type
- valarray/std::valarray::apply
- valarray/std::valarray::cshift
- valarray/std::valarray::free
- valarray/std::valarray::max
- valarray/std::valarray::min
- valarray/std::valarray::resize
- valarray/std::valarray::shift
- valarray/std::valarray::size
- valarray/std::valarray::sum
- valarray/std::valarray::swap
helpviewer_keywords:
- std::valarray [C++]
- std::valarray [C++], value_type
- std::valarray [C++], apply
- std::valarray [C++], cshift
- std::valarray [C++], free
- std::valarray [C++], max
- std::valarray [C++], min
- std::valarray [C++], resize
- std::valarray [C++], shift
- std::valarray [C++], size
- std::valarray [C++], sum
- std::valarray [C++], swap
ms.assetid: 19b862f9-5d09-4003-8844-6ddd02c1a3a7
ms.openlocfilehash: 53b2c2160b522bd28e316eb29f0661447fb84b11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132628"
---
# <a name="valarray-class"></a>valarray 클래스

클래스 템플릿은 고속 `Type` 수치 연산을 수행 하도록 설계 되 고 계산 성능에 최적화 된, 배열로 저장 된 형식의 요소 시퀀스를 제어 하는 개체를 설명 합니다.

## <a name="remarks"></a>설명

이 클래스는 정렬된 값 집합의 수학적 개념을 표현한 것이며 요소는 번호가 0부터 순차적으로 지정됩니다. 이 클래스는 [vector](../standard-library/vector-class.md)와 같은 고급 시퀀스 컨테이너가 지원하는 기능 중 일부를 지원하므로 유사 컨테이너로 설명됩니다. 이는 두 가지 중요 한 측면에서 클래스 템플릿 벡터와 다릅니다.

- `valarray<Type>` *Xarr 같이* = cos ( *yarr*) + sin ( *zarr*)과 같이 형식과 길이가 같은 개체의 해당 요소 간에 다양 한 산술 연산을 정의 합니다.

- `valarray<Type>` [&#91;&#93;연산자 ](#op_at)를 오버 로드 하 여 개체의 첨자를 만드는 다양 한 흥미로운 방법을 정의 합니다.

클래스의 개체 `Type` :

- 기본 동작과 함께 공용 기본 생성자, 소멸자, 복사 생성자 및 대입 연산자를 포함합니다.

- 필요에 따라 기본 동작으로 부동 소수점 형식을 위해 정의된 산술 연산자 및 수학 함수를 정의합니다.

특히 복사본 생성과 뒤에 할당이 이어지는 기본 생성 간에는 차이가 없을 수도 있습니다. 클래스의 개체에 대 한 작업은 `Type` 예외를 throw 할 수 없습니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[valarray](#valarray)|다른 `valarray`의 복사본 또는 다른 `valarray`의 하위 집합으로서 특정 크기, 특정 값의 요소가 있는 `valarray`를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|Name|설명|
|-|-|
|[value_type](#value_type)|`valarray`에 저장된 요소의 형식을 나타내는 형식입니다.|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[적용할](#apply)|`valarray`의 각 요소에 지정된 함수를 적용합니다.|
|[cshift](#cshift)|`valarray`에 있는 모든 요소를 주기적으로 지정된 위치 수만큼 이동합니다.|
|[free](#free)|`valarray`에서 사용하는 메모리를 비웁니다.|
|[max](#max)|`valarray`에서 가장 큰 요소를 찾습니다.|
|[min](#min)|`valarray`에서 가장 작은 요소를 찾습니다.|
|[조정해](#resize)|필요에 따라 요소를 추가 또는 제거하여 `valarray`의 요소 수를 지정된 수로 변경합니다.|
|[shift](#shift)|`valarray`에 있는 모든 요소를 지정된 위치 수만큼 이동합니다.|
|[size](#size)|`valarray`의 요소 수를 찾습니다.|
|[sum](#sum)|0이 아닌 길이의 `valarray`에 있는 모든 요소의 합계를 결정합니다.|
|[스왑을](#swap)||

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자!](#op_not)|`valarray`에 있는 각 요소의 논리적 `NOT` 값을 가져오는 단항 연산자입니다.|
|[연산자% =](#op_mod_eq)|배열 요소를 요소별로 지정된 `valarray`나 요소 형식의 값으로 나눈 나머지를 가져옵니다.|
|[연산자&=](#op_and_eq)|지정된 `valarray`의 해당 요소나 요소 형식의 값으로 배열에 있는 요소의 비트 `AND`를 가져옵니다.|
|[연산자>>=](#op_gt_gt_eq)|`valarray` 피연산자의 각 요소에 대한 비트를 지정된 위치 수 또는 두 번째 `valarray`에 지정된 요소 양만큼 오른쪽으로 이동합니다|
|[연산자<<=](#op_lt_lt_eq)|`valarray` 피연산자의 각 요소에 대한 비트를 지정된 위치 수 또는 두 번째 `valarray`에 지정된 요소 양만큼 왼쪽으로 이동합니다|
|[연산자 * =](#op_star_eq)|요소별로 지정된 `valarray`의 요소나 요소 형식의 값을 피연산자 `valarray`에 곱합니다.|
|[연산자 +](#op_add)|`valarray`의 각 요소에 +를 적용하는 단항 연산자입니다.|
|[operator + =](#op_add_eq)|요소별로, 지정된 `valarray`의 요소나 요소 형식의 값을 피연산자 `valarray`에 더합니다.|
|[연산자](#operator-)|`valarray`의 각 요소에 -를 적용하는 단항 연산자입니다.|
|[연산자-=](#operator-_eq)|요소별로, 지정된 `valarray`의 요소나 요소 형식의 값을 피연산자 `valarray`에서 뺍니다.|
|[operator/=](#op_div_eq)|요소별로 지정된 `valarray`의 요소나 요소 형식의 값을 피연산자 `valarray`에 나눕니다.|
|[연산자 =](#op_eq)|값이 직접 지정되었거나 다른 `valarray`의 일부로 지정되었거나 `slice_array`, `gslice_array`, `mask_array` 또는 `indirect_array`으로 지정된 `valarray`에 요소를 할당합니다.|
|[operator&#91;&#93;](#op_at)|지정된 인덱스 또는 지정된 하위 집합에서 요소 또는 그 값에 대한 참조를 반환합니다.|
|[operator ^ =](#op_xor_eq)|지정된 valarray나 요소 형식의 값이 있는 배열의 요소 전체 배타적 논리 OR 연산자(`XOR`)를 가져옵니다.|
|[연산자&#124;=](#op_or_eq)|지정된 `valarray`의 해당 요소나 요소 형식의 값으로 배열에 있는 요소의 비트 `OR`를 가져옵니다.|
|[연산자 ~](#op_dtor)|`valarray`에 있는 각 요소의 비트에 대한 `NOT` 값을 가져오는 단항 연산자입니다.|

## <a name="apply"></a><a name="apply"></a> 적용할

valarray의 각 요소에 지정된 함수를 적용합니다.

```cpp
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```

### <a name="parameters"></a>매개 변수

*_Func (형식)*\
피연산자 valarray의 각 요소에 적용할 함수 개체입니다.

*_Func (const 형식&)*\
피연산자 valarray의 각 요소에 적용할 const의 함수 개체입니다.

### <a name="return-value"></a>반환 값

해당 요소가 피연산자 valarray의 요소 전체에 `_Func`를 적용했던 valarray

### <a name="remarks"></a>설명

멤버 함수는 길이가 크기 인 [valarray](../standard-library/valarray-class.md)클래스의 개체를 반환 합니다 **\<Type>** . 각 요소는입니다  [](#size) `_Func((*this)[I])` .

### <a name="example"></a>예제

```cpp
// valarray_apply.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

using namespace std;

int __cdecl MyApplyFunc( int n )
{
   return n*2;
}

int main( int argc, char* argv[] )
{
   valarray<int> vaR(10), vaApplied(10);
   int i;

   for ( i = 0; i < 10; i += 3 )
      vaR[i] = i;

   for ( i = 1; i < 10; i += 3 )
      vaR[i] = 0;

   for ( i = 2; i < 10; i += 3 )
      vaR[i] = -i;

   cout << "The initial Right valarray is: (";
   for   ( i=0; i < 10; ++i )
      cout << " " << vaR[i];
   cout << " )" << endl;

   vaApplied = vaR.apply( MyApplyFunc );

   cout << "The element-by-element result of "
       << "applying MyApplyFunc to vaR is the\nvalarray: ( ";
   for ( i = 0; i < 10; ++i )
      cout << " " << vaApplied[i];
   cout << " )" << endl;
}
```

```Output
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )
The element-by-element result of applying MyApplyFunc to vaR is the
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )
```

## <a name="cshift"></a><a name="cshift"></a> cshift

valarray에 있는 모든 요소를 주기적으로 지정된 위치 수만큼 이동합니다.

```cpp
valarray<Type> cshift(int count) const;
```

### <a name="parameters"></a>매개 변수

*수*\
요소를 앞으로 이동할 위치 수입니다.

### <a name="return-value"></a>반환 값

피연산자 valarray의 위치를 기준으로 모든 요소가 이동 된 *count* 위치를 valarray 앞으로 주기적는 새 valarray입니다.

### <a name="remarks"></a>설명

*Count* 값이 양수 이면 왼쪽 *수* 주기적 요소가 이동 합니다.

*Count* 의 음수 값은 주기적 right *count* 위치에 요소를 이동 합니다.

### <a name="example"></a>예제

```cpp
// valarray_cshift.cpp
// compile with: /EHsc

#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;

    valarray<int> va1(10), va2(10);
    for (i = 0; i < 10; i+=1)
        va1[i] = i;
    for (i = 0; i < 10; i+=1)
        va2[i] = 10 - i;

    cout << "The operand valarray va1 is: (";
    for (i = 0; i < 10; i++)
        cout << " " << va1[i];
    cout << ")" << endl;

    // A positive parameter shifts elements right
    va1 = va1.cshift(4);
    cout << "The cyclically shifted valarray va1 is:\nva1.cshift (4) = (";
    for (i = 0; i < 10; i++)
        cout << " " << va1[i];
    cout << ")" << endl;

    cout << "The operand valarray va2 is: (";
    for (i = 0; i < 10; i++)
        cout << " " << va2[i];
    cout << ")" << endl;

    // A negative parameter shifts elements left
    va2 = va2.cshift(-4);
    cout << "The cyclically shifted valarray va2 is:\nva2.shift (-4) = (";
    for (i = 0; i < 10; i++)
        cout << " " << va2[i];
    cout << ")" << endl;
}
```

```Output
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)
The cyclically shifted valarray va1 is:
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)
The cyclically shifted valarray va2 is:
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)
```

## <a name="free"></a><a name="free"></a> 늘릴

valarray에서 사용하는 메모리를 비웁니다.

```cpp
void free();
```

### <a name="remarks"></a>설명

이 비표준 함수를 사용하는 경우의 결과는 빈 valarray를 할당하는 것과 같습니다. 예를 들어:

```cpp
valarray<T> v;
v = valarray<T>();

// equivalent to v.free()
```

## <a name="max"></a><a name="max"></a> 최대값

valarray에서 가장 큰 요소를 찾습니다.

```cpp
Type max() const;
```

### <a name="return-value"></a>반환 값

피연산자 valarray의 요소 최대값입니다.

### <a name="remarks"></a>설명

멤버 함수는 요소에 대해 연산자를 제공 해야 하는 클래스의 요소 쌍 사이에 **\<** or **operator> 연산자** 를 적용 하 여 값을 비교 합니다 `Type` `Type` .

### <a name="example"></a>예제

```cpp
// valarray_max.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i, MaxValue;

   valarray<int> vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  2*i - 1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  10 - i;

   cout << "The operand valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   MaxValue = vaR.max (  );
   cout << "The largest element in the valarray is: "
        << MaxValue  << "." << endl;
}
```

```Output
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).
The largest element in the valarray is: 13.
```

## <a name="min"></a><a name="min"></a>분

valarray에서 가장 작은 요소를 찾습니다.

```cpp
Type min() const;
```

### <a name="return-value"></a>반환 값

피연산자 valarray의 요소 최소값입니다.

### <a name="remarks"></a>설명

멤버 함수는 요소에 대해 연산자를 제공 해야 하는 클래스의 요소 쌍 사이에 **\<** or **operator> 연산자** 를 적용 하 여 값을 비교 합니다 `Type` `Type` .

### <a name="example"></a>예제

```cpp
// valarray_min.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i, MinValue;

   valarray<int> vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  2*i;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  5 - i;

   cout << "The operand valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   MinValue = vaR.min ( );
   cout << "The smallest element in the valarray is: "
        << MinValue  << "." << endl;
}
/* Output:
The operand valarray is: ( 0 2 3 -3 8 0 -6 14 -3 -9 ).
The smallest element in the valarray is: -9.
*/
```

## <a name="operator"></a><a name="op_not"></a> 연산자!

valarray에 있는 각 요소의 논리적 **NOT** 값을 가져오는 단항 연산자입니다.

```cpp
valarray<bool> operator!() const;
```

### <a name="return-value"></a>반환 값

피연산자 valarray의 요소 값에 대한 부정인 부울 값의 valarray

### <a name="remarks"></a>설명

논리 연산 **NOT** 은 모든 0을 1로 변환하며 0이 아닌 모든 값은 1로 간주하여 0으로 변환하므로 요소를 부정합니다. 부울 값의 반환된 valarray는 피연산자 valarray와 크기가 같습니다.

Valarray의 및 요소에 대 한 이진 표현 내에서 개별 비트의 수준을 부정 하는 비트 **not**[valarray:: operator ~](#op_dtor) 도 있습니다 **`char`** **`int`** .

### <a name="example"></a>예제

```cpp
// valarray_op_lognot.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<bool> vaNOT ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaNOT = !vaL;
   cout << "The element-by-element result of "
        << "the logical NOT operator! is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The element-by-element result of the logical NOT operator! is the
valarray: ( 1 1 1 0 1 0 1 0 1 0 ).
```

## <a name="operator"></a><a name="op_mod_eq"></a> 연산자% =

배열 요소를 요소별로 지정된 valarray나 요소 형식의 값으로 나눈 나머지를 가져옵니다.

```cpp
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
요소 전체에서 피연산자 valarray를 나눌 피연산자 valarray의 요소 형식과 동일한 요소 형식의 값 또는 valarray

### <a name="return-value"></a>반환 값

해당 요소가 피연산자 valarray의 요소 단위 나누기의 나머지가 되는 valarray 

### <a name="example"></a>예제

```cpp
// valarray_class_op_rem.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 6 ), vaR ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  53;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -67;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  3*i+1;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL %= vaR;
   cout << "The remainders from the element-by-element "
        << "division is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 53 -67 53 -67 53 -67 ).
The initial  right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
valarray: ( 0 -3 4 -7 1 -3 ).
```

## <a name="operatoramp"></a><a name="op_and_eq"></a> 연산자&amp;=

지정된 valarray의 해당 요소나 요소 형식의 값으로 배열에 있는 요소의 비트 **AND** 를 가져옵니다.

```cpp
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
요소 전체에서 피연산자 valarray를 사용 하 여 결합할 피연산자 valarray의 요소 형식과 동일한 요소 형식의 값 또는 valarray `AND` 입니다.

### <a name="return-value"></a>반환 값

해당 요소가 `AND` 피연산자 valarray의  요소 전체 논리 인 valarray

### <a name="remarks"></a>설명

비트 연산은 및 데이터 형식과 variant의 비트를 조작 하는 데만 사용할 수 있으며,,,,, **`char`** **`int`** **`float`** **`double`**  **`void`** , **`bool`** 또는 보다 복잡 한 기타 데이터 형식은 사용할 수 없습니다.

비트 and는 논리적으로 동일한 참 테이블을 포함 `AND` 하지만 개별 비트 수준에서 데이터 형식에 적용 됩니다. B 1 *및* *b* 2가 지정 된 경우 *b* 1 `AND` *b* 2는 **`true`** 두 비트가 모두 true 이면이 고, 하나 이상 false 이면입니다 **`false`** .

### <a name="example"></a>예제

```cpp
// valarray_class_op_bitand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL &= vaR;
   cout << "The element-by-element result of "
        << "the logical AND operator&= is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&= is the
valarray: ( 0 0 0 2 0 4 0 6 0 8 ).
```

## <a name="operatorgtgt"></a><a name="op_gt_gt_eq"></a> 연산자&gt;&gt;=

valarray 피연산자의 각 요소에 대한 비트를 지정된 위치 수 또는 두 번째 valarray에 지정된 요소 양만큼 오른쪽으로 이동합니다.

```cpp
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
오른쪽으로 이동할 크기를 나타내는 값 또는 해당 요소가 요소 전체 오른쪽 이동 크기를 나타내는 valarray

### <a name="return-value"></a>반환 값

해당 요소가 *오른쪽* 에 지정 된 크기 만큼 오른쪽으로 이동 된 valarray

### <a name="remarks"></a>설명

부호 있는 숫자의 부호는 유지됩니다.

### <a name="example"></a>예제

```cpp
// valarray_class_op_rs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  64;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -64;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial operand valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL >>= vaR;
   cout << "The element-by-element result of "
        << "the right shift is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
```

## <a name="operatorltlt"></a><a name="op_lt_lt_eq"></a> 연산자&lt;&lt;=

valarray 피연산자의 각 요소에 대한 비트를 지정된 위치 수 또는 두 번째 valarray에 지정된 요소 양만큼 왼쪽으로 이동합니다.

```cpp
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
왼쪽으로 이동할 크기를 나타내는 값 또는 해당 요소가 요소 전체 왼쪽 이동 크기를 나타내는 valarray

### <a name="return-value"></a>반환 값

해당 요소가 *오른쪽* 에 지정 된 크기 만큼 왼쪽으로 이동 된 valarray

### <a name="remarks"></a>설명

부호 있는 숫자의 부호는 유지됩니다.

### <a name="example"></a>예제

```cpp
// valarray_class_op_ls.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial operand valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL <<= vaR;
   cout << "The element-by-element result of "
        << "the left shift"
        << endl << "on the operand array is the valarray:"
        << endl << "( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift
on the operand array is the valarray:
( 1 -2 4 -8 16 -32 64 -128 ).
```

## <a name="operator"></a><a name="op_star_eq"></a> 연산자 * =

요소별로 지정된 valarray의 요소나 요소 형식의 값을 피연산자 valarray에 곱합니다.

```cpp
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
요소 전체에서 피연산자 valarray를 곱할 피연산자 valarray의 요소 형식과 동일한 요소 형식의 값 또는 valarray

### <a name="return-value"></a>반환 값

해당 요소가 피연산자 valarray 및 *right* 의 요소 전체 곱 인 valarray

### <a name="example"></a>예제

```cpp
// valarray_op_emult.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL *= vaR;
   cout << "The element-by-element result of "
        << "the multiplication is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
*/
```

## <a name="operator"></a><a name="op_add"></a> 연산자 +

valarray의 각 요소에 +를 적용하는 단항 연산자입니다.

```cpp
valarray<Type> operator+() const;
```

### <a name="return-value"></a>반환 값

해당 요소가 피연산자 배열 요소에 +가 적용된 valarray

### <a name="example"></a>예제

```cpp
// valarray_op_eplus.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<int> vaPLUS ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaPLUS = +vaL;
   cout << "The element-by-element result of "
        << "the operator+ is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaPLUS [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
```

## <a name="operator"></a><a name="op_add_eq"></a> operator + =

요소별로 지정된 valarray의 요소나 요소 형식의 값을 피연산자 valarray에 더합니다.

```cpp
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
요소 전체에서 피연산자 valarray를 더할 피연산자 valarray의 요소 형식과 동일한 요소 형식의 값 또는 valarray

### <a name="return-value"></a>반환 값

해당 요소가 피연산자 valarray와 *right* 의 요소 전체 합계인 valarray입니다.

### <a name="example"></a>예제

```cpp
// valarray_op_eadd.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL += vaR;
   cout << "The element-by-element result of "
        << "the sum is the"
        << endl << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
valarray: ( 2 0 4 2 6 4 8 6 ).
```

## <a name="operator-"></a><a name="operator-"></a> 연산자

valarray의 각 요소에 -를 적용하는 단항 연산자입니다.

```cpp
valarray<Type> operator-() const;
```

### <a name="return-value"></a>반환 값

해당 요소가 피연산자 배열 요소에 -가 적용된 valarray

### <a name="example"></a>예제

```cpp
// valarray_op_eminus.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<int> vaMINUS ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaMINUS = -vaL;
   cout << "The element-by-element result of "
        << "the operator+ is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaMINUS [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).
```

## <a name="operator-"></a><a name="operator-_eq"></a> 연산자-=

요소별로 지정된 valarray의 요소나 요소 형식의 값을 피연산자 valarray에서 뺍니다.

```cpp
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
요소 전체에서 피연산자 valarray에서 뺄 피연산자 valarray의 요소 형식과 동일한 요소 형식의 값 또는 valarray

### <a name="return-value"></a>반환 값

해당 요소가 피연산자 valarray와 *right* 의 요소 전체 차 인 valarray

### <a name="example"></a>예제

```cpp
// valarray_op_esub.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  10;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL -= vaR;
   cout << "The element-by-element result of "
        << "the difference is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
```

## <a name="operator"></a><a name="op_div_eq"></a> operator/=

요소별로 지정된 valarray의 요소나 요소 형식의 값으로 피연산자 valarray를 나눕니다.

```cpp
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
요소 전체에서 피연산자 valarray로 나눌 피연산자 valarray의 요소 형식과 동일한 요소 형식의 값 또는 valarray

### <a name="return-value"></a>반환 값

해당 요소가 피연산자 valarray의 요소 전체 몫 인 valarray를 *오른쪽* 으로 나눈 값입니다.

### <a name="example"></a>예제

```cpp
// valarray_op_ediv.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<double> vaL ( 6 ), vaR ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  100;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -100;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  2*i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL /= vaR;
   cout << "The element-by-element result of "
        << "the quotient is the"
        << endl << "valarray: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
valarray: ( inf -50 25 -16.6667 12.5 -10 ).
```

## <a name="operator"></a><a name="op_eq"></a> 연산자 =

해당 값이 직접 지정되거나 다른 valarray의 일부분으로 또는 slice_array, gslice_array, mask_array, indirect_array에 의해 지정되는 요소를 valarray에 할당합니다.

```cpp
valarray<Type>& operator=(const valarray<Type>& right);

valarray<Type>& operator=(valarray<Type>&& right);

valarray<Type>& operator=(const Type& val);

valarray<Type>& operator=(const slice_array<Type>& _Slicearray);

valarray<Type>& operator=(const gslice_array<Type>& _Gslicearray);

valarray<Type>& operator=(const mask_array<Type>& _Maskarray);

valarray<Type>& operator=(const indirect_array<Type>& _Indarray);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
피연산자 valarray에 복사할 valarray

*짧은*\
피연산자 valarray의 요소에 할당할 값

*_Slicearray*\
피연산자 valarray에 복사할 slice_array

*_Gslicearray*\
피연산자 valarray에 복사할 gslice_array

*_Maskarray*\
피연산자 valarray에 복사할 mask_array

*_Indarray*\
피연산자 valarray에 복사할 indirect_array

### <a name="return-value"></a>반환 값

첫 번째 멤버 연산자는 제어 되는 시퀀스를 *right* 로 제어 되는 시퀀스의 복사본으로 바꿉니다.

두 번째 구성원 연산자도 첫 번째 구성원 연산자와 동일하지만 [Rvalue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 포함합니다.

세 번째 멤버 연산자는 제어 되는 시퀀스의 각 요소를 *val* 의 복사본으로 바꿉니다.

나머지 구성원 연산자는 해당 인수가 선택한 제어되는 시퀀스의 요소를 대체합니다. 이러한 요소는 [operator&#91;&#93;](#op_at)를 통해서만 생성됩니다.

대체 제어되는 시퀀스의 구성원 값이 초기 제어되는 시퀀스의 구성원에 따라 달라지는 경우에는 결과가 정의되지 않습니다.

### <a name="remarks"></a>설명

제어되는 시퀀스의 길이가 변경되면 대개 결과가 정의되지 않습니다. 그러나 이 구현에서는 단순히 제어되는 시퀀스의 요소에 대한 참조나 포인터만 무효화됩니다.

### <a name="example"></a>예제

```cpp
// valarray_op_assign.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 1 )
      va [ i ] = i;
   for ( i = 0 ; i < 10 ; i+=1 )
      vaR [ i ] = 10 -  i;

   cout << "The operand valarray va is:";
   for ( i = 0 ; i < 10 ; i++ )
      cout << " " << va [ i ];
   cout << endl;

   cout << "The operand valarray vaR is:";
      for ( i = 0 ; i < 10 ; i++ )
         cout << " " << vaR [ i ];
   cout << endl;

   // Assigning vaR to va with the first member functon
   va = vaR;
   cout << "The reassigned valarray va is:";
   for ( i = 0 ; i < 10 ; i++ )
      cout << " " << va [ i ];
   cout << endl;

   // Assigning elements of value 10 to va
   // with the second member functon
   va = 10;
   cout << "The reassigned valarray va is:";
      for ( i = 0 ; i < 10 ; i++ )
         cout << " " << va [ i ];
   cout << endl;
}
```

```Output
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10

```

## <a name="operator"></a><a name="op_at"></a> operator[]

지정된 인덱스 또는 지정된 하위 집합에서 요소 또는 그 값에 대한 참조를 반환합니다.

```cpp
Type& operator[](size_t _Off);

slice_array<Type> operator[](slice _Slicearray);

gslice_array<Type> operator[](const gslice& _Gslicearray);

mask_array<Type> operator[](const valarray<bool>& _Boolarray);

indirect_array<Type> operator[](const valarray<size_t>& _Indarray);

Type operator[](size_t _Off) const;

valarray<Type> operator[](slice _Slice) const;

valarray<Type> operator[](const gslice& _Gslicearray) const;

valarray<Type> operator[](const valarray<bool>& _Boolarray) const;

valarray<Type> operator[](const valarray<size_t>& _Indarray) const;
```

### <a name="parameters"></a>매개 변수

*_Off*\
값을 할당할 요소의 인덱스

*_Slicearray*\
선택하거나 새 valarray로 반환할 하위 집합을 지정하는 valarray의 slice_array

*_Gslicearray*\
선택하거나 새 valarray로 반환할 하위 집합을 지정하는 valarray의 gslice_array

*_Boolarray*\
선택하거나 새 valarray로 반환할 하위 집합을 지정하는 valarray의 bool_array

*_Indarray*\
선택하거나 새 valarray로 반환할 하위 집합을 지정하는 valarray의 indirect_array

### <a name="return-value"></a>반환 값

지정된 인덱스 또는 지정된 하위 집합에서 요소 또는 그 값에 대한 참조

### <a name="remarks"></a>설명

멤버 연산자는 <strong> \* 이</strong>에 의해 제어 되는 요소 중에서 요소 시퀀스를 선택할 수 있는 여러 가지 방법을 제공 하도록 오버 로드 됩니다. 첫 번째 5개 연산자 그룹은 [operator=](#op_eq) 및 기타 할당 연산자의 다양한 오버로드와 함께 작동하여 제어되는 시퀀스의 선택적 교체(조각화)를 허용합니다. 이 경우 선택한 요소가 있어야 합니다.

1 또는 2로 정의된 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)을 사용하여 컴파일한 경우 valarray 범위를 벗어난 요소에 액세스하면 런타임 오류가 발생합니다.  자세한 내용은 [확인된 반복기](../standard-library/checked-iterators.md)를 참조하세요.

### <a name="example"></a>예제

연산자를 선언하고 사용하는 방법의 예제는 [slice::slice](../standard-library/slice-class.md#slice) 및 [gslice::gslice](../standard-library/gslice-class.md#gslice)의 예제를 참조하세요.

## <a name="operator"></a><a name="op_xor_eq"></a> operator ^ =

지정된 valarray나 요소 형식의 값이 있는 배열의 요소별 배타적 논리 OR 연산자(**XOR**)를 가져옵니다.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
요소 전체에서 배타적 논리 **XOR** 을 통해 피연산자 valarray와 결합할 피연산자 valarray의 요소 형식과 동일한 요소 형식의 값 또는 valarray

### <a name="return-value"></a>반환 값

해당 요소가 피연산자 valarray 및 *right* 의 요소 전체 배타적 논리적 **XOR** 인 valarray

### <a name="remarks"></a>설명

배타적 논리합 ( **XOR**)은 다음과 같은 의미 체계를 가집니다. *e* 1과 *e* 2를 지정 하면 *e* 1 **XOR** *e* 2는 요소 중 **`true`** 정확히 하나가 true 이면이 고, 두 요소 모두 false 이면이 고, **`false`** 두 요소가 모두 true 이면입니다.

### <a name="example"></a>예제

```cpp
// valarray_op_exor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;

    valarray<int> vaL ( 10 ), vaR ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL [ i ] =  1;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL [ i ] =  0;
    for ( i = 0 ; i < 10 ; i += 3 )
        vaR [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 3 )
        vaR [ i ] =  i-1;
    for ( i = 2 ; i < 10 ; i += 3 )
        vaR [ i ] =  i-1;

    cout << "The initial operand valarray is:  ( ";
        for (i = 0 ; i < 10 ; i++ )
            cout << vaL [ i ] << " ";
    cout << ")." << endl;

    cout << "The  right valarray is: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaR [ i ] << " ";
    cout << ")." << endl;

    vaL ^= vaR;
    cout << "The element-by-element result of "
        << "the bitwise XOR operator^= is the"
        << endl << "valarray: ( ";
        for (i = 0 ; i < 10 ; i++ )
            cout << vaL [ i ] << " ";
    cout << ")." << endl;
}
```

```Output
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^= is the
valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
```

## <a name="operator124"></a><a name="op_or_eq"></a> 연산자&#124;=

지정된 valarray의 해당 요소나 요소 형식의 값으로 배열에 있는 요소의 비트 `OR`을 가져옵니다.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
요소 전체에서 비트 `OR`을 통해 피연산자 valarray와 결합할 피연산자 valarray의 요소 형식과 동일한 요소 형식의 값 또는 valarray

### <a name="return-value"></a>반환 값

해당 요소가 `OR` 피연산자 valarray의 요소 전체 비트 배열인 valarray

### <a name="remarks"></a>설명

비트 연산은 및 데이터 형식과 variant의 비트를 조작 하는 데만 사용할 수 있으며,,,,, **`char`** **`int`** **`float`** **`double`**  **`void`** , **`bool`** 또는 보다 복잡 한 기타 데이터 형식은 사용할 수 없습니다.

비트 `OR`은 논리적 `OR`과 같은 진리표를 포함하지만 개별 비트 수준에서 데이터 형식에 적용됩니다. B 1 *및* *b* 2가 지정 된 경우 *b* 1 `OR` *b* 2는 비트 중 하나 이상이 true 이면이 **`true`** 고, **`false`** 두 비트가 모두 false 이면입니다.

### <a name="example"></a>예제

```cpp
// valarray_class_op_bitor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial operand valarray is:"
        << endl << "( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is:"
        << endl << "( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL |= vaR;
   cout << "The element-by-element result of "
        << "the logical OR"
        << endl << "operator|= is the valarray:"
        << endl << "( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial operand valarray is:
( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is:
( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the logical OR
operator|= is the valarray:
( 1 0 1 3 3 4 7 6 7 9 ).
```

## <a name="operator"></a><a name="op_dtor"></a> 연산자 ~

`NOT`Valarray에 있는 각 요소의 비트 값을 가져오는 단항 연산자입니다.

```cpp
valarray<Type> operator~() const;
```

### <a name="return-value"></a>반환 값

`NOT`피연산자 valarray의 요소 값에 대 한 비트 값인 부울 값의 valarray입니다.

### <a name="remarks"></a>설명

비트 연산은 및 데이터 형식과 variant의 비트를 조작 하는 데만 사용할 수 있으며,,,,,, **`char`** **`int`** **`float`** **`double`**  **`void`** **`bool`** 또는 기타 복잡 한 데이터 형식은 사용할 수 없습니다.

비트 `NOT`은 논리적 `NOT`과 같은 진리표를 포함하지만 개별 비트 수준에서 데이터 형식에 적용됩니다. *b* 를 지정하는 경우 ~ *b* 는 *b* 가 false이면 true이고 *b* 가 true이면 false입니다. 논리적 **NOT**[operator!](#op_not)는 는 요소 수준에 적용 되 고 0이 아닌 모든 값을로 계산 **`true`** 하며, 결과는 부울 값의 valarray입니다. `NOToperator~`이와 반대로 비트 연산은 비트 연산의 결과에 따라 0 또는 1이 아닌 값의 valarray를 발생 시킬 수 있습니다.

### <a name="example"></a>예제

```cpp
// valarray_op_bitnot.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;

    valarray<unsigned short int> vaL1 ( 10 );
    valarray<unsigned short int> vaNOT1 ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL1 [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL1 [ i ] =  5*i;

    cout << "The initial valarray <unsigned short int> is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaL1 [ i ] << " ";
    cout << ")." << endl;

    vaNOT1 = ~vaL1;
    cout << "The element-by-element result of "
        << "the bitwise NOT operator~ is the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT1 [ i ] << " ";
    cout << ")." << endl << endl;

    valarray<int> vaL2 ( 10 );
    valarray<int> vaNOT2 ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL2 [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL2 [ i ] =  -2 * i;

    cout << "The initial valarray <int> is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaL2 [ i ] << " ";
    cout << ")." << endl;

    vaNOT2 = ~vaL2;
    cout << "The element-by-element result of "
        << "the bitwise NOT operator~ is the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT2 [ i ] << " ";
    cout << ")." << endl;

    // The negative numbers are represented using
    // the two's complement approach, so adding one
    // to the flipped bits returns the negative elements
    vaNOT2 = vaNOT2 + 1;
    cout << "The element-by-element result of "
        << "adding one"
        << endl << "is the negative of the "
        << "original elements the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT2 [ i ] << " ";
    cout << ")." << endl;
}
```

```Output
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).
The element-by-element result of the bitwise NOT operator~ is the
valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).

The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).
The element-by-element result of the bitwise NOT operator~ is the
valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).
The element-by-element result of adding one
is the negative of the original elements the
valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).
```

## <a name="resize"></a><a name="resize"></a> 조정해

valarray의 요소 수를 지정된 수로 변경합니다.

```cpp
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,
    const Type val);
```

### <a name="parameters"></a>매개 변수

*_Newsize*\
크기 조정된 valarray의 요소 수입니다.

*짧은*\
크기 조정된 valarray의 요소에 지정할 값입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 기본 생성자를 사용하여 요소를 초기화합니다.

제어된 시퀀스의 요소에 대한 모든 포인터 또는 참조가 무효화됩니다.

### <a name="example"></a>예제

다음 예제에서는 valarray::resize 멤버 함수의 사용을 보여 줍니다.

```cpp
// valarray_resize.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;
    size_t size1, sizeNew;

    valarray<int> va1(10);
    for (i = 0; i < 10; i+=1)
        va1[i] = i;

    cout << "The valarray contains ( ";
        for (i = 0; i < 10; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;

    size1 = va1.size();
    cout << "The number of elements in the valarray is: "
         << size1  << "." <<endl << endl;

    va1.resize(15, 10);

    cout << "The valarray contains ( ";
        for (i = 0; i < 15; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;
    sizeNew = va1.size();
    cout << "The number of elements in the resized valarray is: "
         << sizeNew  << "." <<endl << endl;
}
```

```Output
The valarray contains ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray is: 10.

The valarray contains ( 10 10 10 10 10 10 10 10 10 10 10 10 10 10 10 ).
The number of elements in the resized valarray is: 15.
```

## <a name="shift"></a><a name="shift"></a> 교대조

valarray에 있는 모든 요소를 지정된 위치 수만큼 이동합니다.

```cpp
valarray<Type> shift(int count) const;
```

### <a name="parameters"></a>매개 변수

*수*\
요소를 앞으로 이동할 위치 수입니다.

### <a name="return-value"></a>반환 값

피연산자 valarray의 위치와 관련 하 여 모든 요소가 valarray 앞 *으로 이동 하* 는 새 valarray입니다.

### <a name="remarks"></a>설명

*Count* 값이 양수 이면 왼쪽의 요소 *수가* 0으로 채워집니다.

*Count* 의 음수 값은 0으로 채우기를 사용 하 여 요소 오른쪽 *개수* 위치를 이동 합니다.

### <a name="example"></a>예제

```cpp
// valarray_shift.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va1 ( 10 ), va2 ( 10 );
   for ( i = 0 ; i < 10 ; i += 1 )
      va1 [ i ] =  i;
   for ( i = 0 ; i < 10 ; i += 1 )
      va2 [ i ] = 10 -  i;

   cout << "The operand valarray va1(10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   // A positive parameter shifts elements left
   va1 = va1.shift ( 4 );
   cout << "The shifted valarray va1 is: va1.shift (4) = ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   cout << "The operand valarray va2(10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;

   // A negative parameter shifts elements right
   va2 = va2.shift ( - 4 );
   cout << "The shifted valarray va2 is: va2.shift (-4) = ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).
```

## <a name="size"></a><a name="size"></a> 크기가

valarray에 있는 요소 수를 찾습니다.

```cpp
size_t size() const;
```

### <a name="return-value"></a>반환 값

피연산자 valarray에 있는 요소 수입니다.

### <a name="example"></a>예제

다음 예제에서는 valarray:: size 멤버 함수의 사용을 보여 줍니다.

```cpp
// valarray_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;
    size_t size1, size2;

    valarray<int> va1(10), va2(12);
    for (i = 0; i < 10; i += 1)
        va1[i] =  i;
    for (i = 0; i < 10; i += 1)
        va2[i] =  i;

    cout << "The operand valarray va1(10) is: ( ";
        for (i = 0; i < 10; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;

    size1 = va1.size();
    cout << "The number of elements in the valarray va1 is: va1.size = "
         << size1  << "." <<endl << endl;

    cout << "The operand valarray va2(12) is: ( ";
        for (i = 0; i < 10; i++)
            cout << va2[i] << " ";
    cout << ")." << endl;

    size2 = va2.size();
    cout << "The number of elements in the valarray va2 is: va2.size = "
         << size2  << "." << endl << endl;

    // Initializing two more elements to va2
    va2[10] = 10;
    va2[11] = 11;
    cout << "After initializing two more elements,\n"
         << "the operand valarray va2(12) is now: ( ";
        for (i = 0; i < 12; i++)
            cout << va2[i] << " ";
    cout << ")." << endl;
    cout << "The number of elements in the valarray va2 is still: "
         << size2  << "." << endl;
}
```

```Output
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray va1 is: va1.size = 10.

The operand valarray va2(12) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray va2 is: va2.size = 12.

After initializing two more elements,
the operand valarray va2(12) is now: ( 0 1 2 3 4 5 6 7 8 9 10 11 ).
The number of elements in the valarray va2 is still: 12.
```

## <a name="sum"></a><a name="sum"></a> 총합

0이 아닌 길이의 valarray에 있는 모든 요소의 합계를 결정합니다.

```cpp
Type sum() const;
```

### <a name="return-value"></a>반환 값

피연산자 valarray의 요소 합입니다.

### <a name="remarks"></a>설명

길이가 1 보다 큰 경우 멤버 함수는 클래스의 요소 쌍 사이에를 적용 하 여 합계에 값을 추가 `operator+=` `Type` 합니다. 즉, 형식의 요소에 대해 필요한 연산자를 제공 합니다 `Type` .

### <a name="example"></a>예제

```cpp
// valarray_sum.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    int sumva = 0;

    valarray<int> va ( 10 );
    for ( i = 0 ; i < 10 ; i+=1 )
        va [ i ] =  i;

    cout << "The operand valarray va (10) is: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;

    sumva = va.sum ( );
    cout << "The sum of elements in the valarray is: "
        << sumva  << "." <<endl;
}
```

```Output
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The sum of elements in the valarray is: 45.
```

## <a name="swap"></a><a name="swap"></a> 스왑을

두 `valarray`의 요소를 교환합니다.

```cpp
void swap(valarray& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 요소를 제공하는 `valarray`입니다.

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 **`*this`** 과 *오른쪽* 으로 바꿉니다. 일정한 시간에 이 작업을 수행하고, 예외를 throw하지 않고, 두 개의 제어된 시퀀스에서 요소를 지정하는 참조, 포인터 또는 반복기를 무효화하지 않습니다.

## <a name="valarray"></a><a name="valarray"></a> valarray

특정 크기, 특정 값의 요소, 다른 valarray의 복사본 또는 다른 valarray의 하위 요소인 valarray를 생성합니다.

```cpp
valarray();

explicit valarray(
    size_t Count);

valarray(
    const Type& Val,
    size_t Count);

valarray(
    const Type* Ptr,
    size_t Count);

valarray(
    const valarray<Type>& Right);

valarray(
    const slice_array<Type>& SliceArray);

valarray(
    const gslice_array<Type>& GsliceArray);

valarray(
    const mask_array<Type>& MaskArray);

valarray(
    const indirect_array<Type>& IndArray);

valarray(
    valarray<Type>&& Right);

valarray(
    initializer_list<Type> IList);
```

### <a name="parameters"></a>매개 변수

*수*\
valarray에 지정할 요소의 수입니다.

*짧은*\
valarray의 요소를 초기화하는 데 사용할 값입니다.

*Ptr*\
valarray의 요소를 초기화하는 데 사용할 값에 대한 포인터입니다.

*오른쪽*\
새 valarray를 초기화할 기존 valarray입니다.

*SliceArray*\
생성 중인 valarray의 요소를 초기화하는 데 사용할 요소 값을 포함하는 slice_array입니다.

*GsliceArray*\
생성 중인 valarray의 요소를 초기화하는 데 사용할 요소 값을 포함하는 gslice_array입니다.

*MaskArray*\
생성 중인 valarray의 요소를 초기화하는 데 사용할 요소 값을 포함하는 mask_array입니다.

*IndArray*\
생성 중인 valarray의 요소를 초기화하는 데 사용할 요소 값을 포함하는 indirect_array입니다.

*IList*\
복사할 요소를 포함하는 initializer_list입니다.

### <a name="remarks"></a>설명

첫 번째(기본) 생성자는 개체를 빈 배열로 초기화합니다. 다음 세 가지 생성자는 각각 다음과 같이 개체를 *Count* 요소의 배열로 초기화 합니다.

- 명시적 `valarray(size_t Count)`의 경우 각 요소는 기본 생성자를 사용하여 초기화됩니다.

- 의 경우 `valarray(const Type& Val, Count)` 각 요소는 *Val* 을 사용 하 여 초기화 됩니다.

- `valarray(const Type* Ptr, Count)`의 경우 `I` 위치의 요소는 `Ptr`[`I`]로 초기화됩니다.

나머지 각 생성자는 \<Type> 인수에 지정 된 하위 집합에 의해 결정 되는 valarray 개체로 개체를 초기화 합니다.

마지막 생성자도 그 앞의 생성자와 마찬가지이지만 [Rvalue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 사용합니다.

### <a name="example"></a>예제

```cpp
// valarray_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;

    // The second member function
    valarray<int> va(10);
    for (auto i : va){
        va[i] = 2 * (i + 1);
    }

    cout << "The operand valarray va is:\n(";
    for (auto i : va) {
        cout << " " << va[i];
    }
    cout << " )" << endl;

    slice Slice(2, 4, 3);

    // The fifth member function
    valarray<int> vaSlice = va[Slice];

    cout << "The new valarray initialized from the slice is vaSlice =\n"
        << "va[slice( 2, 4, 3)] = (";
    for (int i = 0; i < 3; i++) {
        cout << " " << vaSlice[i];
    }
    cout << " )" << endl;

    valarray<int> va2{{ 1, 2, 3, 4 }};
    for (auto& v : va2) {
        cout << v << " ";
    }
    cout << endl;
}
```

```Output
The operand valarray va is:
( 0 2 2 2 2 2 2 2 2 2 )
The new valarray initialized from the slice is vaSlice =
va[slice( 2, 4, 3)] = ( 0 0 0 )
1 2 3 4
```

## <a name="value_type"></a><a name="value_type"></a> value_type

valarray에 저장된 요소의 형식을 나타내는 형식입니다.

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Type`의 동의어입니다.

### <a name="example"></a>예제

```cpp
// valarray_value_type.cpp
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

    // value_type declaration and initialization:
    valarray<int>::value_type Right = 10;

    cout << "The decalared value_type Right is: "
            << Right << endl;
    va *= Right;
    cout << "The resulting valarray is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;
}
```

```Output
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).
The decalared value_type Right is: 10
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
