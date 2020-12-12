---
description: '자세한 정보: &lt; 새 &gt; 연산자 및 열거형'
title: '&lt;새 &gt; 연산자 및 열거형'
ms.date: 11/04/2016
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
ms.openlocfilehash: e5b6a675b200c80dc56778a66d63d5940561eb1a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338181"
---
# <a name="ltnewgt-operators-and-enums"></a>&lt;새 &gt; 연산자 및 열거형

## <a name="enum-align_val_t"></a><a name="op_align_val_t"></a> 열거형 align_val_t

```cpp
enum class align_val_t : size_t {};
```

## <a name="operator-delete"></a><a name="op_delete"></a> operator delete

개체의 개별에 대 한 저장소 할당을 취소 하기 위해 delete 식에서 호출 하는 함수입니다.

```cpp
void operator delete(void* ptr) throw();
void operator delete(void *, void*) throw();
void operator delete(void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>매개 변수

*ptr*\
삭제에 의해 값이 무효 처리되는 포인터입니다.

### <a name="remarks"></a>설명

첫 번째 함수는 *ptr* 의 값을 잘못 된 값으로 렌더링 하기 위해 delete 식에 의해 호출 됩니다. 프로그램은 C++ 표준 라이브러리를 통해 정의되는 기본 버전을 바꾸는 함수를 이 함수 시그니처로 정의할 수 있습니다. 필요한 동작은 null 이거나 [operator new](../standard-library/new-operators.md#op_new)(**size_t**)에 대 한 이전 호출에서 반환 된 *ptr* 값을 허용 하는 것입니다.

*Ptr* 의 null 값에 대 한 기본 동작은 아무 작업도 수행 하지 않는 것입니다. 다른 모든 *ptr* 값은 앞에서 설명한 대로 호출에서 반환 되는 값 이어야 합니다. 이러한 null이 아닌 *ptr* 값의 기본 동작은 이전 호출에서 할당 된 저장소를 회수 하는 것입니다. 이러한 회수 된 저장소의 일부나 전체가 (size_t)에 대 한 후속 호출 `operator new` 또는 ( `calloc` **size_t**), `malloc` ( **size_t**) 또는 `realloc` ( **`void`** <strong>\*</strong> **size_t**)에 의해 할당 되는 조건에 따라 지정 되지 않습니다.

두 번째 함수는 **`new`** ( **std:: size_t**) 형식의 새 식에 해당 하는 placement delete 식에 의해 호출 됩니다. 아무 작업도 수행하지 않습니다.

세 번째 함수는 **`new`** ( **std:: size_t**, **conststd:: nothrow_t&**) 형식의 새 식에 해당 하는 placement delete 식에 의해 호출 됩니다. 프로그램은 C++ 표준 라이브러리를 통해 정의되는 기본 버전을 바꾸는 함수를 이 함수 시그니처로 정의할 수 있습니다. 필요한 동작은 이전 `operator new`( **size_t**) 호출에 의해 반환되었거나 null인 `ptr`의 값을 허용하는 것입니다. 기본 동작은 ()를 평가 하는 것입니다 **`delete`** `ptr` .

### <a name="example"></a>예제

**Operator delete** 를 사용 하는 예제는 [operator new](../standard-library/new-operators.md#op_new) 를 참조 하세요.

## <a name="operator-delete"></a><a name="op_delete_arr"></a> operator delete []

개체 배열에 대해 스토리지를 할당 해제하기 위해 delete 식에서 호출되는 함수입니다.

```cpp
void operator delete[](void* ptr) throw();
void operator delete[](void *, void*) throw();
void operator delete[](void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>매개 변수

*ptr*\
삭제에 의해 값이 무효 처리되는 포인터입니다.

### <a name="remarks"></a>설명

첫 번째 함수는 `delete[]` 잘못 된 *ptr* 값을 렌더링 하기 위해 식에 의해 호출 됩니다. 프로그램은 C++ 표준 라이브러리를 통해 정의되는 기본 버전을 바꾸는 함수를 이 함수 시그니처로 정의할 수 있으므로 함수는 교체 가능합니다. 필요한 동작은 null 이거나 [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)(**size_t**)에 대 한 이전 호출에서 반환 된 *ptr* 값을 허용 하는 것입니다. *Ptr* 의 null 값에 대 한 기본 동작은 아무 작업도 수행 하지 않는 것입니다. 다른 모든 *ptr* 값은 앞에서 설명한 대로 호출에서 반환 되는 값 이어야 합니다. 이러한 null이 아닌 *ptr* 값의 기본 동작은 이전 호출에서 할당 된 저장소를 회수 하는 것입니다. 이러한 회수 된 저장소의 일부 또는 전체가 [operator new](../standard-library/new-operators.md#op_new)(**size_t**)에 대 한 후속 호출 또는 ( `calloc` **size_t**), `malloc` (**size_t**) 또는 `realloc` ( **`void`** <strong>\*</strong> , **size_t**)에 대 한 후속 호출에 의해 할당 되는 조건에 따라 지정 되지 않습니다.

두 번째 함수는 `delete[]` `new[]` `new[]` (**std:: size_t**) 형식의 식에 해당 하는 배치 식에 의해 호출 됩니다. 아무 작업도 수행하지 않습니다.

세 번째 함수는 `new[]`( **std::size_t**, **const std::nothrow_t&**) 형식의 `new[]` 식에 해당하는 placement delete 식에 의해 호출됩니다. 프로그램은 C++ 표준 라이브러리를 통해 정의되는 기본 버전을 바꾸는 함수를 이 함수 시그니처로 정의할 수 있습니다. 필요한 동작은 null 이거나 연산자에 대 한 이전  호출 `new[]` (**size_t**)에서 반환 된 ptr 값을 허용 하는 것입니다. 기본 동작은 `delete[]`( `ptr`)를 평가하는 것입니다.

### <a name="example"></a>예제

`operator delete[]` 사용 방법의 예제는 [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)를 참조하세요.

## <a name="operator-new"></a><a name="op_new"></a> operator new

개별 개체에 대해 스토리지를 할당하기 위해 new 식에서 호출되는 함수입니다.

```cpp
void* operator new(std::size_t count) throw(bad_alloc);
void* operator new(std::size_t count, const std::nothrow_t&) throw();
void* operator new(std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>매개 변수

*수*\
할당할 스토리지의 바이트 수입니다.

*ptr*\
반환할 포인터입니다.

### <a name="return-value"></a>반환 값

새로 할당된 스토리지의 가장 낮은 바이트 주소에 대한 포인터입니다. 또는 *ptr*.

### <a name="remarks"></a>설명

첫 번째 함수는 `count` 바이트의 스토리지를 할당하기 위해 new 식에서 호출되며, 해당 크기의 모든 개체를 나타내도록 적절하게 정렬됩니다. 프로그램은 C++ 표준 라이브러리를 통해 정의되는 기본 버전을 바꾸며 대체 가능한 대체 함수를 이 함수 시그니처로 정의할 수 있습니다.

필요한 동작은 저장소를 요청으로 할당할 수 있는 경우에만 null이 아닌 포인터를 반환 하는 것입니다. 이러한 각 할당에서는 할당된 다른 스토리지에서 스토리지를 분리하는 포인터가 생성됩니다. 연속 호출을 통해 할당되는 스토리지의 순서와 연속성은 지정되지 않습니다. 저장된 초기값은 지정되지 않습니다. 반환되는 포인터는 할당된 스토리지의 시작 위치(최저 바이트 주소)를 가리킵니다. count가 0이면 반환되는 값은 함수가 반환하는 다른 값과 비교 시 동일하지 않습니다.

기본 동작은 루프를 실행하는 것입니다. 루프 내에서 함수는 먼저 요청된 스토리지 할당을 시도합니다. 이 시도에서 `malloc`( **size_t**)를 호출하는지 여부는 지정되지 않습니다. 이 시도가 성공하면 함수는 할당된 스토리지에 대한 포인터를 반환합니다. 그렇지 않으면 함수는 지정된 [새 처리기](../standard-library/new-typedefs.md#new_handler)를 호출합니다. 호출된 함수가 반환되면 루프는 반복됩니다. 요청된 스토리지 할당 시도가 성공하거나 호출된 함수가 반환되지 않으면 루프는 종료됩니다.

새 처리기에 필요한 동작은 다음 작업 중 하나를 수행하는 것입니다.

- 더 많은 스토리지를 할당 가능하도록 지정한 다음, 반환됩니다.

- 또는 중 하나를 호출 `abort` `exit` 합니다.

- 형식의 개체를 Throw `bad_alloc` 합니다.

[새 처리기](../standard-library/new-typedefs.md#new_handler)의 기본 동작은 `bad_alloc` 형식의 개체를 throw하는 것입니다. null 포인터가 기본 새 처리기를 지정합니다.

(Size_t)에 대 한 후속 호출로 할당 된 저장소의 순서와 근접성은 해당 `operator new` 값에 저장 된 초기 값과 마찬가지로 지정 되지 않습니다.

두 번째 함수는 `count` 바이트의 스토리지를 할당하기 위해 placement new 식에서 호출되며, 해당 크기의 모든 개체를 나타내도록 적절하게 정렬됩니다. 프로그램은 C++ 표준 라이브러리를 통해 정의되는 기본 버전을 바꾸며 대체 가능한 대체 함수를 이 함수 시그니처로 정의할 수 있습니다.

기본 동작은 `operator new` 해당 함수가 성공 하는 경우 ()를 반환 하는 것입니다 `count` . 그렇지 않으면 null 포인터가 반환됩니다.

세 번째 함수는 형식의 배치 식에 의해 호출 됩니다 **`new`** `new ( args ) T` . 여기에서 *args* 는 단일 개체 포인터로 구성됩니다. 이 포인터는 알려진 주소에 개체를 생성하는 데 유용할 수 있습니다. 함수는 *ptr* 을 반환합니다.

**Operator new** 에서 할당 한 저장소를 해제 하려면 [delete 연산자](../standard-library/new-operators.md#op_delete)를 호출 합니다.

New의 throw 또는 throw 되지 않는 동작에 대 한 자세한 내용은 [new 및 Delete 연산자](../cpp/new-and-delete-operators.md)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// new_op_new.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;

class MyClass
{
public:
   MyClass( )
   {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass( )
   {
      imember = 0; cout << "Destructing MyClass." << this << endl;
   };
   int imember;
};

int main( )
{
   // The first form of new delete
   MyClass* fPtr = new MyClass;
   delete fPtr;

   // The second form of new delete
   MyClass* fPtr2 = new( nothrow ) MyClass;
   delete fPtr2;

   // The third form of new delete
   char x[sizeof( MyClass )];
   MyClass* fPtr3 = new( &x[0] ) MyClass;
   fPtr3 -> ~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;
}
```

## <a name="operator-new"></a><a name="op_new_arr"></a> operator new []

개체 배열에 대해 스토리지를 할당하기 위해 new 식에서 호출되는 할당 함수입니다.

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);
void* operator new[](std::size_t count, const std::nothrow_t&) throw();
void* operator new[](std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>매개 변수

*수*\
배열 개체에 대해 할당할 스토리지의 바이트 수입니다.

*ptr*\
반환할 포인터입니다.

### <a name="return-value"></a>반환 값

새로 할당된 스토리지의 가장 낮은 바이트 주소에 대한 포인터입니다. 또는 *ptr*.

### <a name="remarks"></a>설명

첫 번째 함수는 `count` 바이트의 스토리지를 할당하기 위해 `new[]` 식에서 호출되며, 해당 크기 이하의 모든 개체를 나타내도록 적절하게 정렬됩니다. 프로그램은 C++ 표준 라이브러리를 통해 정의되는 기본 버전을 바꾸는 함수를 이 함수 시그니처로 정의할 수 있습니다. 필요한 동작은 [operator new](../standard-library/new-operators.md#op_new)(**size_t**)와 동일 합니다. 기본 동작은 `operator new`( `count`)를 반환하는 것입니다.

두 번째 함수는 `count` 바이트의 스토리지를 할당하기 위해 placement `new[]` 식에서 호출되며, 해당 크기의 모든 배열 개체를 나타내도록 적절하게 정렬됩니다. 프로그램은 C++ 표준 라이브러리를 통해 정의되는 기본 버전을 바꾸는 함수를 이 함수 시그니처로 정의할 수 있습니다. 기본 동작은 해당 함수가 성공 하는 경우 **operatornew**()를 반환 하는 것입니다 `count` . 그렇지 않으면 null 포인터가 반환됩니다.

세 번째 함수는 `new[]` **`new`** ( *args*) **T**[ **N**] 형식의 배치 식에 의해 호출 됩니다. 여기에서 *args* 는 단일 개체 포인터로 구성됩니다. 함수에서 `ptr`을 반환합니다.

`operator new[]`에서 할당하는 스토리지를 비우려면 [operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)를 호출합니다.

new의 throw 또는 비throw 동작에 대한 자세한 내용은 [new 및 delete 연산자](../cpp/new-and-delete-operators.md)를 참조하세요.

### <a name="example"></a>예제

```cpp
// new_op_alloc.cpp
// compile with: /EHsc
#include <new>
#include <iostream>

using namespace std;

class MyClass {
public:
   MyClass() {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass() {
      imember = 0; cout << "Destructing MyClass." << this << endl;
      };
   int imember;
};

int main() {
   // The first form of new delete
   MyClass* fPtr = new MyClass[2];
   delete[ ] fPtr;

   // The second form of new delete
   char x[2 * sizeof( MyClass ) + sizeof(int)];

   MyClass* fPtr2 = new( &x[0] ) MyClass[2];
   fPtr2[1].~MyClass();
   fPtr2[0].~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;

   // The third form of new delete
   MyClass* fPtr3 = new( nothrow ) MyClass[2];
   delete[ ] fPtr3;
}
```
