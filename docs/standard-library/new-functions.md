---
description: '자세히 알아보기: &lt; 새 &gt; 함수'
title: '&lt;new&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: b46a21223fcee4f1e208f97e087e47445d5526c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338189"
---
# <a name="ltnewgt-functions"></a>&lt;new&gt; 함수

## <a name="get_new_handler"></a><a name="get_new_handler"></a> get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>설명

현재 `new_handler`를 반환합니다.

## <a name="launder"></a><a name="launder"></a> launder

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>매개 변수

*ptr*\
*T* 와 유사한 형식의 개체를 보유 하는 메모리의 바이트 주소입니다.

### <a name="return-value"></a>반환 값

X를 가리키는 *T \** 형식의 값입니다.

### <a name="remarks"></a>설명

포인터 최적화 장벽을 라고도 합니다.

상수 식에 인수 값을 사용할 수 있는 경우 상수 식으로 사용 됩니다. 다른 개체에서 사용 하는 저장소 내에 있는 경우 개체를 가리키는 포인터 값을 통해 저장소 바이트에 도달할 수 있습니다.

### <a name="example"></a>예제

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a><a name="nothrow"></a> nothrow

및 버전의 인수로 사용할 개체를 제공 합니다 **`nothrow`** **`new`** **`delete`** .

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>설명

이 개체는 매개 변수 형식 [std::nothrow_t](../standard-library/nothrow-t-structure.md)의 일치를 확인하기 위한 함수 인수로 사용됩니다.

### <a name="example"></a>예제

`std::nothrow_t`를 함수 매개 변수로 사용하는 방법의 예제는 [operator new](../standard-library/new-operators.md#op_new) 및 [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)를 참조하세요.

## <a name="set_new_handler"></a><a name="set_new_handler"></a> set_new_handler

**Operator new** 가 메모리 할당 시도에 실패할 때 호출 되는 사용자 함수를 설치 합니다.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>매개 변수

*Pnew*\
`new_handler`설치할입니다.

### <a name="return-value"></a>반환 값

첫 번째 호출의 경우 0이고 후속 호출의 경우 이전 `new_handler`입니다.

### <a name="remarks"></a>설명

함수는 유지 관리 하는 정적 [새 처리기](../standard-library/new-typedefs.md#new_handler) 포인터에 *pnew* 를 저장 한 다음 포인터에 이전에 저장 된 값을 반환 합니다. 새 처리기는 [new 연산자](../standard-library/new-operators.md#op_new)(**size_t**)에서 사용 됩니다.

### <a name="example"></a>예제

```cpp
// new_set_new_handler.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;
void __cdecl newhandler( )
{
   cout << "The new_handler is called:" << endl;
   throw bad_alloc( );
   return;
}

int main( )
{
   set_new_handler (newhandler);
   try
   {
      while ( 1 )
      {
         new int[5000000];
         cout << "Allocating 5000000 ints." << endl;
      }
   }
   catch ( exception e )
   {
      cout << e.what( ) << endl;
   }
}
```

```Output
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
The new_handler is called:
bad allocation
```
