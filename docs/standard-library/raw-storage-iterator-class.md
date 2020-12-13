---
description: Raw_storage_iterator 클래스에 대해 자세히 알아보세요.
title: raw_storage_iterator 클래스
ms.date: 11/04/2016
f1_keywords:
- memory/std::raw_storage_iterator
- memory/std::raw_storage_iterator::element_type
- memory/std::raw_storage_iterator::iter_type
helpviewer_keywords:
- std::raw_storage_iterator [C++]
- std::raw_storage_iterator [C++], element_type
- std::raw_storage_iterator [C++], iter_type
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
ms.openlocfilehash: fd397de39118a5aa47ea45a8da0052937958bd17
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337921"
---
# <a name="raw_storage_iterator-class"></a>raw_storage_iterator 클래스

초기화되지 않은 메모리에 결과를 저장하는 알고리즘을 사용할 수 있도록 제공되는 어댑터 클래스입니다.

## <a name="syntax"></a>구문

```cpp
template <class OutputIterator, class Type>
    class raw_storage_iterator
```

### <a name="parameters"></a>매개 변수

*OutputIterator*\
저장되는 개체에 대한 출력 반복기를 지정합니다.

*입력할*\
스토리지를 할당할 개체 형식입니다.

## <a name="remarks"></a>설명

클래스는 생성 하는 시퀀스에서 형식의 개체를 생성 하는 출력 반복기를 설명 합니다 `Type` . 클래스의 개체는 `raw_storage_iterator` \< **ForwardIterator**, **Type**> 개체를 생성할 때 지정 하는 클래스의 전방 반복기 개체를 통해 저장소에 액세스 `ForwardIterator` 합니다. 클래스의 첫 번째 개체의 경우 `ForwardIterator` 식은 **& \* 먼저** 생성 된 시퀀스에서 다음 개체 (형식)에 대해 생성 되지 않은 저장소를 지정 해야 합니다 `Type` .

이 어댑터 클래스는 메모리 할당 및 개체 생성을 구분하는 데 필요한 경우에 사용됩니다. `raw_storage_iterator`를 사용하여 `malloc` 함수를 통해 할당된 메모리와 같은 초기화되지 않은 스토리지에 개체를 복사할 수 있습니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|지정된 기본 출력 반복기를 사용하여 원시 스토리지 반복기를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|Name|설명|
|-|-|
|[element_type](#element_type)|원시 스토리지 반복기를 저장할 요소를 설명하는 형식을 제공합니다.|
|[iter_type](#iter_type)|원시 스토리지 반복기의 기반이 되는 반복기를 설명하는 형식을 제공합니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자](#op_star)|출력 반복기 식을 구현 하는 데 사용 되는 역참조 연산자 \* `ii`  =  `x` 입니다.|
|[연산자 =](#op_eq)|\* `i`  =  메모리에 저장 하기 위한 원시 저장소 반복기 식을 구현 하는 데 사용 되는 할당 연산자 `x` 입니다.|
|[operator + +](#op_add_add)|원시 스토리지 반복기에 대한 사전 증가 및 사후 증가 연산자입니다.|

### <a name="element_type"></a><a name="element_type"></a> element_type

원시 스토리지 반복기를 저장할 요소를 설명하는 형식을 제공합니다.

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>설명

형식은 raw_storage_iterator 클래스 템플릿 매개 변수의 동의어입니다 `Type` .

### <a name="iter_type"></a><a name="iter_type"></a> iter_type

원시 스토리지 반복기의 기반이 되는 반복기를 설명하는 형식을 제공합니다.

```cpp
typedef ForwardIterator iter_type;
```

#### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `ForwardIterator`의 동의어입니다.

### <a name="operator"></a><a name="op_star"></a> 연산자\*

원시 저장소 반복기 식 ii x를 구현 하는 데 사용 되는 역참조 연산자 \*   =  입니다.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

#### <a name="return-value"></a>반환 값

원시 스토리지 반복기에 대한 참조

#### <a name="remarks"></a>설명

에 대 한 요구 사항은 `ForwardIterator` 원시 저장소 반복기가 충족 해야 하는 것은 ii t 식만 유효 해야 하 \*   =   고 **`operator`** 또는 자체에 대해서는 아무 것도 표시 하지 않아야 한다는 것입니다 `operator=` . 이 구현의 멤버 연산자는 **\* this** 를 반환 하므로 [operator =](#op_eq)(**constType**&)는 ptr과 같은 식의 실제 저장소를 수행할 수 있습니다 \*   =  `val` .

#### <a name="example"></a>예제

```cpp
// raw_storage_iterator_op_deref.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };

   Int &operator=(int i)
   {
      if (!bIsConstructed)
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl;
      x = i;
      return *this;
   };

   int x;

private:
   bool bIsConstructed;
};

int main( void)
{
   Int *pInt = ( Int* ) malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;
*pInt = 5;
   raw_storage_iterator< Int*, Int > it( pInt );
*it = 5;
}
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="operator"></a><a name="op_eq"></a> 연산자 =

\*   =  메모리에 저장 하기 위해 원시 저장소 반복기 식 i *x* 를 구현 하는 데 사용 되는 할당 연산자입니다.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

#### <a name="parameters"></a>매개 변수

*짧은*\
메모리에 삽입할 형식 개체의 값입니다 `Type` .

#### <a name="return-value"></a>반환 값

연산자는 `val`을 메모리에 삽입한 다음 원시 스토리지 반복기에 대한 참조를 반환합니다.

#### <a name="remarks"></a>설명

`ForwardIterator`원시 저장소 반복기가 충족 해야 하는 상태에 대 한 요구 사항에는 \* *ii*  =  *t* 식만 유효 해야 하며 또는에 대 한 자세한 내용은 고유 하지 않습니다 **`operator`** `operator=` . 이러한 멤버 연산자는 **`*this`** 를 반환 합니다.

대입 연산자는 `first` placement new 식을 평가 하 여 저장 된 반복기 값을 사용 하 여 출력 시퀀스에서 다음 개체를 생성 합니다 `new ( (void*) & *first ) Type( val )` .

#### <a name="example"></a>예제

```cpp
// raw_storage_iterator_op_assign.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int( int i )
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if ( !bIsConstructed )
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl; x = i;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( void )
{
   Int *pInt = ( Int* )malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;

*pInt = 5;

   raw_storage_iterator<Int*, Int> it( pInt );
*it = 5;
}
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="operator"></a><a name="op_add_add"></a> operator + +

원시 스토리지 반복기에 대한 사전 증가 및 사후 증가 연산자입니다.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

#### <a name="return-value"></a>반환 값

원시 스토리지 반복기 또는 원시 스토리지 반복기에 대한 참조입니다.

#### <a name="remarks"></a>설명

첫 번째 연산자는 궁극적으로 연결 된 입력 스트림에서 형식의 개체를 추출 하 고 저장 하려고 `CharType` 합니다. 두 번째 연산자는 개체의 복사본을 만들고 개체를 증가시킨 다음 복사본을 반환합니다.

첫 번째 사전 증가 연산자는 저장 된 출력 반복기 개체를 증가 시킨 다음 **\* 반환 합니다**.

두 번째 사후 증가 연산자는 **\* 이** 의 복사본을 만들고 저장 된 출력 반복기 개체를 증가 시킨 다음 복사본을 반환 합니다.

생성자는를 `first` 출력 반복기 개체로 저장 합니다.

#### <a name="example"></a>예제

```cpp
// raw_storage_iterator_op_incr.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

int main( void )
{
   int *pInt = new int[5];
   std::raw_storage_iterator<int*,int> it( pInt );
   for ( int i = 0; i < 5; i++, it++ ) {
      *it = 2 * i;
   };

   for ( int i = 0; i < 5; i++ ) cout << "array " << i << " = " << pInt[i] << endl;;

   delete[] pInt;
}
```

```Output
array 0 = 0
array 1 = 2
array 2 = 4
array 3 = 6
array 4 = 8
```

### <a name="raw_storage_iterator"></a><a name="raw_storage_iterator"></a> raw_storage_iterator

지정된 기본 출력 반복기를 사용하여 원시 스토리지 반복기를 생성합니다.

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

#### <a name="parameters"></a>매개 변수

*기본*\
생성 중인 `raw_storage_iterator`의 기준으로 사용할 정방향 반복기입니다.

#### <a name="example"></a>예제

```cpp
// raw_storage_iterator_ctor.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if (!bIsConstructed)
         cout << "Error! I'm not constructed!\n";
      cout << "Copying " << i << endl;  x = i; return *this;
   };
   int x;
   bool bIsConstructed;
};

int main( void )
{
   std::list<int> l;
   l.push_back( 1 );
   l.push_back( 2 );
   l.push_back( 3 );
   l.push_back( 4 );

   Int *pInt = (Int*)malloc(sizeof(Int)*l.size( ));
   memset (pInt, 0, sizeof(Int)*l.size( ));
   // Hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ), pInt );  // C4996
   for (unsigned int i = 0; i < l.size( ); i++)
      cout << "array " << i << " = " << pInt[i].x << endl;;

   memset (pInt, 0, sizeof(Int)*l.size( ));
   // hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ),
      std::raw_storage_iterator<Int*,Int>(pInt));  // C4996
   for (unsigned int i = 0; i < l.size( ); i++ )
      cout << "array " << i << " = " << pInt[i].x << endl;

   free(pInt);
}
```

```Output
Error! I'm not constructed!
Copying 1
Error! I'm not constructed!
Copying 2
Error! I'm not constructed!
Copying 3
Error! I'm not constructed!
Copying 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
Constructing 1
Constructing 2
Constructing 3
Constructing 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
```
