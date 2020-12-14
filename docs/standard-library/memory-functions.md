---
description: '자세히 알아보기: &lt; 메모리 &gt; 함수'
title: '&lt;memory&gt; 함수'
ms.date: 08/05/2019
f1_keywords:
- memory/std::addressof
- memory/std::align
- memory/std::allocate_shared
- memory/std::const_pointer_cast
- memory/std::declare_no_pointers
- memory/std::declare_reachable
- memory/std::dynamic_pointer_cast
- memory/std::get_deleter
- memory/std::get_pointer_safety
- memory/std::get_temporary_buffer
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- memory/std::reinterpret_pointer_cast
- memory/std::return_temporary_buffer
- xmemory/std::return_temporary_buffer
- memory/std::static_pointer_cast
- memory/std::swap
- memory/std::undeclare_no_pointers
- memory/std::undeclare_reachable
- memory/std::uninitialized_copy
- memory/std::uninitialized_copy_n
- memory/std::uninitialized_fill
- memory/std::uninitialized_fill_n
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
helpviewer_keywords:
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::swap [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
ms.openlocfilehash: 13c18ce754a3e88d7ad2ae47ead522bc21cec718
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183973"
---
# <a name="ltmemorygt-functions"></a>&lt;memory&gt; 함수

## <a name="addressof"></a><a name="addressof"></a> addressof

개체의 실제 주소를 가져옵니다.

```cpp
template <class T>
T* addressof(
    T& value) noexcept;    // before C++17

template <class T>
constexpr T* addressof(
    T& value) noexcept;    // C++17

template <class T>
const T* addressof(
    const T&& value) = delete;   // C++17
```

### <a name="parameters"></a>매개 변수

*기본값*\
실제 주소를 가져올 개체 또는 함수입니다.

### <a name="return-value"></a>반환 값

오버 로드 된가 있는 경우에도 *값* 이 참조 하는 개체 또는 함수의 실제 주소입니다 `operator&()` .

### <a name="remarks"></a>설명

## <a name="align"></a><a name="align"></a> 않아

지정 된 맞춤 사양에 따라 지정 된 크기의 저장소를 지정 된 저장소의 첫 번째 가능한 주소에 맞춥니다.

```cpp
void* align(
    size_t alignment, // input
    size_t size,      // input
    void*& ptr,       // input/output
    size_t& space     // input/output
);
```

### <a name="parameters"></a>매개 변수

*할당*\
시도에 맞게 정렬됩니다.

*크기가*\
정렬된 스토리지의 크기(바이트 단위)입니다.

*ptr*\
사용 가능한 인접 스토리지 풀 중 사용할 스토리지 풀의 시작 주소입니다. 이 매개 변수는 출력 매개 변수 이기도 하며 정렬이 성공한 경우 새 시작 주소를 포함 하도록 설정 됩니다. `align()`가 실패 한 경우이 매개 변수는 수정 되지 않습니다.

*공간*\
정렬된 스토리지를 만드는 데 사용하기 위해 `align()`에서 사용할 수 있는 총 공간입니다. 이 매개 변수는 출력 매개 변수이기도 하며, 정렬된 스토리지 및 관련된 모든 연결된 오버헤드를 차감한 후 스토리지 버퍼에 남아 있는 조정된 공간을 포함합니다.

`align()`가 실패 한 경우이 매개 변수는 수정 되지 않습니다.

### <a name="return-value"></a>반환 값

요청 된 정렬 된 버퍼가 사용 가능한 공간에 맞지 않는 경우 null 포인터입니다. 그렇지 않으면 *ptr* 의 새 값입니다.

### <a name="remarks"></a>설명

수정 된 *ptr* 및 *space* 매개 변수를 사용 하 여 `align()` 동일한 버퍼에서 반복적으로 호출할 수 있으며 *맞춤* 및 *크기* 값이 서로 다를 수 있습니다. 다음 코드 조각은 `align()`을 사용하는 방법을 보여 줍니다.

```cpp
#include <type_traits> // std::alignment_of()
#include <memory>
//...
char buffer[256]; // for simplicity
size_t alignment = std::alignment_of<int>::value;
void * ptr = buffer;
std::size_t space = sizeof(buffer); // Be sure this results in the true size of your buffer

while (std::align(alignment, sizeof(MyObj), ptr, space)) {
    // You now have storage the size of MyObj, starting at ptr, aligned on
    // int boundary. Use it here if you like, or save off the starting address
    // contained in ptr for later use.
    // ...
    // Last, move starting pointer and decrease available space before
    // the while loop restarts.
    ptr = reinterpret_cast<char*>(ptr) + sizeof(MyObj);
    space -= sizeof(MyObj);
}
// At this point, align() has returned a null pointer, signaling it is not
// possible to allow more aligned storage in this buffer.
```

## <a name="allocate_shared"></a><a name="allocate_shared"></a> allocate_shared

지정 된 할당자를 사용 하 여 지정 된 형식에 대해 할당 되 고 생성 되는 개체에 대 한 [shared_ptr](shared-ptr-class.md) 를 만듭니다. `shared_ptr`를 반환합니다.

```cpp
template <class T, class Allocator, class... Args>
shared_ptr<T> allocate_shared(
    Allocator alloc,
    Args&&... args);
```

### <a name="parameters"></a>매개 변수

*#c4*\
개체를 만드는 데 사용된 할당자입니다.

*args*\
개체가 되는 0개 이상의 인수입니다.

### <a name="remarks"></a>설명

함수는 `shared_ptr<T>` `T(args...)` 할당 및 할당에 의해 생성 되는에 대 한 포인터인 개체를 만듭니다.

## <a name="atomic_compare_exchange_strong"></a><a name="atomic_compare_exchange_strong"></a> atomic_compare_exchange_strong

```cpp
template<class T>
bool atomic_compare_exchange_strong(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_weak"></a><a name="atomic_compare_exchange_weak"></a> atomic_compare_exchange_weak

```cpp
template<class T>
bool atomic_compare_exchange_weak(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a> atomic_compare_exchange_strong_explicit

```cpp
template<class T>
bool atomic_compare_exchange_strong_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_compare_exchange_weak_explicit"></a><a name="atomic_compare_exchange_weak_explicit"></a> atomic_compare_exchange_weak_explicit

```cpp
template<class T>
bool atomic_compare_exchange_weak_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a> atomic_exchange

```cpp
template<class T>
shared_ptr<T> atomic_exchange(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a> atomic_exchange_explicit

```cpp
template<class T>
shared_ptr<T> atomic_exchange_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="atomic_is_lock_free"></a><a name="atomic_is_lock_free"></a> atomic_is_lock_free

```cpp
template<class T>
bool atomic_is_lock_free(
    const shared_ptr<T>* u);
```

## <a name="atomic_load"></a><a name="atomic_load"></a> atomic_load

```cpp
template<class T>
shared_ptr<T> atomic_load(
    const shared_ptr<T>* u);
```

## <a name="atomic_load_explicit"></a><a name="atomic_load_explicit"></a> atomic_load_explicit

```cpp
template<class T>
shared_ptr<T> atomic_load_explicit(
    const shared_ptr<T>* u,
    memory_order mo);
```

## <a name="atomic_store"></a><a name="atomic_store"></a> atomic_store

```cpp
template<class T>
void atomic_store(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_store_explicit"></a><a name="atomic_store_explicit"></a> atomic_store_explicit

```cpp
template<class T>
void atomic_store_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="const_pointer_cast"></a><a name="const_pointer_cast"></a> const_pointer_cast

[Shared_ptr](shared-ptr-class.md)에 대 한 Const 캐스트입니다.

```cpp
template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>매개 변수

*트*\
반환된 공유 포인터에 의해 제어되는 형식입니다.

*다른*\
인수 공유 포인터에 의해 제어되는 형식입니다.

*sp-2*\
인수 공유 포인터입니다.

### <a name="remarks"></a>설명

가 null 포인터를 반환 하면 템플릿 함수는 빈 개체를 반환 하 `shared_ptr` `const_cast<T*>(sp.get())` 고, 그렇지 않으면 `shared_ptr<T>` *sp* 에서 소유 하는 리소스를 소유 하는 개체를 반환 합니다. `const_cast<T*>(sp.get())` 식이 유효해야 합니다.

### <a name="example"></a>예제

```cpp
// std__memory__const_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int);
    std::shared_ptr<const int> sp1 =
        std::const_pointer_cast<const int>(sp0);

    *sp0 = 3;
    std::cout << "sp1 == " << *sp1 << std::endl;

    return (0);
}
```

```Output
sp1 == 3
```

## <a name="declare_no_pointers"></a><a name="declare_no_pointers"></a> declare_no_pointers

기본 주소 포인터와 블록 크기로 정의된 메모리 블록에 있는 문자에 추적 가능한 포인터가 포함될 수 없음을 가비지 수집기에 알립니다.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>매개 변수

*ptr*\
추적 가능한 포인터를 더 이상 포함하지 않는 첫 번째 문자의 주소입니다.

*크기가*\
추적 가능한 포인터를 포함 하지 않는 *ptr* 에서 시작 하는 블록의 크기입니다.

### <a name="remarks"></a>설명

함수는 범위에 있는 주소에 `[ ptr, ptr + size)` 추적 가능한 포인터가 더 이상 포함 되지 않음을 가비지 수집기에 알립니다. 할당 된 저장소에 대 한 모든 포인터는 연결할 수 없는 경우에만 역참조 되어야 합니다.

## <a name="declare_reachable"></a><a name="declare_reachable"></a> declare_reachable

지정된 주소가 할당된 스토리지에 대한 것이며 접근할 수 있음을 가비지 컬렉션에 알립니다.

```cpp
void declare_reachable(
    void* ptr);
```

### <a name="parameters"></a>매개 변수

*ptr*\
연결할 수 있는 할당된 유효한 스토리지 영역에 대한 포인터입니다.

### <a name="remarks"></a>설명

*Ptr* 이 null이 아닌 경우 함수는 *ptr* 에 현재 연결할 수 있음을 알립니다. 즉, 유효한 할당 된 저장소를 가리킵니다.

## <a name="default_delete"></a><a name="default_delete"></a> default_delete

**New 연산자** 를 사용 하 여 할당 된 개체를 삭제 합니다. [Unique_ptr](unique-ptr-class.md)와 함께 사용 하기에 적합 합니다.

```cpp
struct default_delete
{
    constexpr default_delete() noexcept = default;

    template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
    default_delete(const default_delete<Other>&) noexcept;

    void operator()(T* ptr) const noexcept;
};
```

### <a name="parameters"></a>매개 변수

*ptr*\
삭제할 개체에 대한 포인터입니다.

*다른*\
삭제할 배열의 요소 형식입니다.

### <a name="remarks"></a>설명

클래스 템플릿에서는 **new 연산자** 를 사용 하 여 할당 된 스칼라 개체를 삭제 하는 deleter을 설명 합니다 `unique_ptr` . 이 템플릿 클래스에는 명시적 특수화 `default_delete<T[]>`도 있습니다.

## <a name="destroy_at"></a><a name="destroy_at"></a> destroy_at

```cpp
template <class T>
void destroy_at(
    T* location);
```

`location->~T()`와 동일합니다.

## <a name="destroy"></a><a name="destroy"></a> 삭제

```cpp
template <class ForwardIterator>
void destroy(
    ForwardIterator first,
    ForwardIterator last);
```

다음과 동일 합니다.

```cpp
for (; first != last; ++first)
    destroy_at(addressof(*first));
```

## <a name="destroy_n"></a><a name="destroy_n"></a> destroy_n

```cpp
template <class ForwardIterator, class Size>
ForwardIterator destroy_n(
    ForwardIterator first,
    Size count);
```

다음과 동일 합니다.

```cpp
for (; count > 0; (void)++first, --count)
    destroy_at(addressof(*first));
return first;
```

## <a name="dynamic_pointer_cast"></a><a name="dynamic_pointer_cast"></a> dynamic_pointer_cast

[Shared_ptr](shared-ptr-class.md)로 동적 캐스팅 합니다.

```cpp
template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>매개 변수

*트*\
반환된 공유 포인터에 의해 제어되는 형식입니다.

*다른*\
인수 공유 포인터에 의해 제어되는 형식입니다.

*sp-2*\
인수 공유 포인터입니다.

### <a name="remarks"></a>설명

가 null 포인터를 반환 하면 템플릿 함수는 빈 개체를 반환 하 `shared_ptr` `dynamic_cast<T*>(sp.get())` 고, 그렇지 않으면 `shared_ptr<T>` *sp* 에서 소유 하는 리소스를 소유 하는 개체를 반환 합니다. `dynamic_cast<T*>(sp.get())` 식이 유효해야 합니다.

### <a name="example"></a>예제

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::dynamic_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="get_deleter"></a><a name="get_deleter"></a> get_deleter

[Shared_ptr](shared-ptr-class.md)에서 deleter을 가져옵니다.

```cpp
template <class Deleter, class T>
Deleter* get_deleter(
    const shared_ptr<T>& sp) noexcept;
```

### <a name="parameters"></a>매개 변수

*Deleter*\
삭제자의 형식입니다.

*트*\
공유 포인터에 의해 제어되는 형식입니다.

*sp-2*\
공유 포인터입니다.

### <a name="remarks"></a>설명

템플릿 함수는 sp 개체에 속하는 *deleter* 형식의 deleter에 대 한 포인터를 반환 `shared_ptr` 합니다 . *Sp* 에 deleter가 없거나 해당 Deleter가 *deleter* 형식이 아닌 경우 함수는 0을 반환 합니다.

### <a name="example"></a>예제

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct deleter
{
    void operator()(base *pb)
    {
        delete pb;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->value = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->value = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}
```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a><a name="get_pointer_safety"></a> get_pointer_safety

모든 가비지 수집기에서 간주된 포인터 안전 형식을 반환합니다.

```cpp
pointer_safety get_pointer_safety() noexcept;
```

### <a name="remarks"></a>설명

함수는 자동 가비지 수집기에서 가정 하는 포인터 안전 형식을 반환 합니다.

## <a name="get_temporary_buffer"></a><a name="get_temporary_buffer"></a> get_temporary_buffer

지정 된 수의 요소를 초과 하지 않는 요소의 시퀀스에 대 한 임시 저장소를 할당 합니다.

```cpp
template <class T>
pair<T *, ptrdiff_t> get_temporary_buffer(
    ptrdiff_t count);
```

### <a name="parameters"></a>매개 변수

*수*\
메모리를 할당하도록 요청한 최대 요소 수입니다.

### <a name="return-value"></a>반환 값

첫 번째 구성 요소는 할당된 메모리에 대한 포인터이고, 두 번째 구성 요소는 저장할 수 있는 요소의 최대 수를 나타내는 버퍼의 크기를 제공하는 `pair`입니다.

### <a name="remarks"></a>설명

이 함수는 메모리에 대한 요청을 만들며 성공하지 못할 수 있습니다. 버퍼가 할당되지 않은 경우 함수는 두 번째 구성 요소는 0이고 첫 번째 구성 요소는 null 포인터인 쌍을 반환합니다.

임시 메모리에 대해서만이 함수를 사용 합니다.

### <a name="example"></a>예제

```cpp
// memory_get_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
        << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
        << "could store is given by: resultPair.second = "
        << resultPair.second << "." << endl;
}
```

```Output
The number of integers in the array is: 9.
The number of elements that the allocated memory
could store is given by: resultPair.second = 9.
```

## <a name="make_shared"></a><a name="make_shared"></a> make_shared

기본 할당자를 사용 하 여 0 개 이상의 인수에서 생성 된 할당 된 개체를 가리키는 [shared_ptr](shared-ptr-class.md) 를 만들어 반환 합니다. 지정된 형식의 개체와 `shared_ptr`을 모두 할당 및 생성하여 개체의 공유 소유권을 관리하고 `shared_ptr`을 반환합니다.

```cpp
template <class T, class... Args>
shared_ptr<T> make_shared(
    Args&&... args);
```

### <a name="parameters"></a>매개 변수

*args*\
0개 이상의 생성자 인수입니다. 이 함수는 제공되는 인수에 따라 호출할 생성자 오버로드를 유추합니다.

### <a name="remarks"></a>설명

`make_shared`를 개체 및 `shared_ptr`을 만드는 간단하고 보다 효율적인 방법으로 사용하여 개체에 대한 공유 액세스를 동시에 관리할 수 있습니다. 의미상으로 다음 두 문은 동일합니다.

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

그러나 첫 번째 문은 두 개의 할당을 만들고, `shared_ptr` 개체의 할당이 성공한 후에 `Example`의 할당이 실패하면 명명되지 않은 `Example` 개체가 유출됩니다. `make_shared`를 사용하는 문은 관련된 함수 호출이 하나뿐이므로 더 간단합니다. 라이브러리가 개체와 스마트 포인터에 대해 단일 할당을 만들 수 있으므로 더 효율적입니다. 이 함수를 통해 더 빠르고 메모리 조각화를 줄일 수 있으며 한 할당에 대 한 예외는 발생 하지 않습니다. 개체를 참조하고 스마트 포인터의 참조 카운트를 업데이트하는 코드에 대한 집약성이 더 높아지므로 성능이 향상됩니다.

개체에 대 한 공유 액세스가 필요 하지 않은 경우 [make_unique](memory-functions.md#make_unique) 를 사용 하는 것이 좋습니다. 개체에 대한 사용자 지정 할당자를 지정해야 하는 경우에는 [allocate_shared](memory-functions.md#allocate_shared)를 사하세요. `make_shared`Deleter를 인수로 전달할 방법이 없으므로 개체에 사용자 지정 deleter가 필요한 경우를 사용할 수 없습니다.

다음 예에서는 특정 생성자 오버로드를 호출하여 형식에 대한 공유 포인터를 만드는 방법을 보여 줍니다.

### <a name="example"></a>예제

```cpp
// stl_make_shared.cpp
// Compile by using: cl /W4 /EHsc stl_make_shared.cpp
#include <iostream>
#include <string>
#include <memory>
#include <vector>

class Song {
public:
    std::wstring title_;
    std::wstring artist_;

    Song(std::wstring title, std::wstring artist) : title_(title), artist_(artist) {}
    Song(std::wstring title) : title_(title), artist_(L"Unknown") {}
};

void CreateSharedPointers()
{
    // Okay, but less efficient to have separate allocations for
    // Song object and shared_ptr control block.
    auto song = new Song(L"Ode to Joy", L"Beethoven");
    std::shared_ptr<Song> sp0(song);

    // Use make_shared function when possible. Memory for control block
    // and Song object are allocated in the same call:
    auto sp1 = std::make_shared<Song>(L"Yesterday", L"The Beatles");
    auto sp2 = std::make_shared<Song>(L"Blackbird", L"The Beatles");

    // make_shared infers which constructor to use based on the arguments.
    auto sp3 = std::make_shared<Song>(L"Greensleeves");

    // The playlist vector makes copies of the shared_ptr pointers.
    std::vector<std::shared_ptr<Song>> playlist;
    playlist.push_back(sp0);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    playlist.push_back(sp3);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    for (auto&& sp : playlist)
    {
        std::wcout << L"Playing " << sp->title_ <<
            L" by " << sp->artist_ << L", use count: " <<
            sp.use_count() << std::endl;
    }
}

int main()
{
    CreateSharedPointers();
}
```

이 예에서는 다음과 같은 출력을 생성합니다.

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a><a name="make_unique"></a> make_unique

지정된 인수를 사용하여 생성되는, 지정된 형식의 개체에 대한 [unique_ptr](unique-ptr-class.md)을 만들고 반환합니다.

```cpp
// make_unique<T>
template <class T, class... Args>
unique_ptr<T> make_unique(Args&&... args);

// make_unique<T[]>
template <class T>
unique_ptr<T> make_unique(size_t size);

// make_unique<T[N]> disallowed
template <class T, class... Args>
/* unspecified */ make_unique(Args&&...) = delete;
```

### <a name="parameters"></a>매개 변수

*트*\
`unique_ptr`이 가리키는 개체의 형식입니다.

*Args*\
*Args* 로 지정 된 생성자 인수의 형식입니다.

*args*\
*T* 형식의 개체 생성자에 전달할 인수입니다.

*elements*\
*T* 형식의 요소 배열입니다.

*크기가*\
새 배열에 공간을 할당할 수 있는 요소의 수입니다.

### <a name="remarks"></a>설명

첫 번째 오버 로드는 단일 개체에 사용 됩니다. 두 번째 오버 로드는 배열에 대해 호출 됩니다. 세 번째 오버 로드는 형식 인수 (make_unique)에서 배열 크기를 지정 하는 것을 방지 합니다. \<T[N]> 이 생성은 현재 표준에서 지원 되지 않습니다. `make_unique`를 사용하여 배열에 대한 `unique_ptr`을 만드는 경우 배열 요소를 별도로 초기화해야 합니다. 이 오버 로드를 사용 하는 대신 [std:: vector](vector-class.md)를 사용 하는 것이 더 적합할 수 있습니다.

`make_unique`는 예외 안전성을 위해 신중하게 구현되기 때문에 `make_unique` 생성자를 직접 호출하는 대신 `unique_ptr`를 사용할 것을 추천합니다.

### <a name="example"></a>예제

다음 예제에서는 `make_unique`을 사용하는 방법을 보여 줍니다. 더 많은 예제는 [방법: unique_ptr 인스턴스 만들기 및 사용](../cpp/how-to-create-and-use-unique-ptr-instances.md)을 참조하세요.

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

`unique_ptr`과 관련하여 오류 C2280이 표시되는 경우 대부분 삭제된 함수인 해당 복사 생성자를 호출하려고 했기 때문입니다.

## <a name="owner_less"></a><a name="owner_less"></a> owner_less

공유된 포인터와 약한 포인트에 대한 소유권 기반의 혼합된 비교를 허용합니다. **`true`** 멤버 함수에서 왼쪽 매개 변수가 right 매개 변수 앞에 정렬 되 면를 반환 합니다 `owner_before` .

```cpp
template <class T>
    struct owner_less; // not defined

template <class T>
struct owner_less<shared_ptr<T>>
{
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;
};

template <class T>
struct owner_less<weak_ptr<T>>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;
};

template<> struct owner_less<void>
{
    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;
};
```

### <a name="parameters"></a>매개 변수

*비어*\
공유 또는 약한 포인터입니다.

*오른쪽*\
공유 또는 약한 포인터입니다.

### <a name="remarks"></a>설명

클래스 템플릿은 모든 멤버 연산자를를 반환 하는 것으로 정의 합니다 `left.owner_before(right)` .

## <a name="reinterpret_pointer_cast"></a><a name="reinterpret_pointer_cast"></a> reinterpret_pointer_cast

`shared_ptr`캐스트를 사용 하 여 기존 공유 포인터에서 새를 만듭니다.

```cpp
template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    const shared_ptr<U>& ptr) noexcept;

template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    shared_ptr<U>&& ptr) noexcept;
```

### <a name="parameters"></a>매개 변수

*ptr*\
에 대 한 참조 `shared_ptr<U>` 입니다.

### <a name="remarks"></a>설명

*Ptr* 이 비어 있으면 새 `shared_ptr` 도 비어 있고, 그렇지 않은 경우에는 *ptr* 을 사용 하 여 소유권을 공유 합니다. 새 공유 포인터는를 평가한 결과입니다 `reinterpret_cast<Y*>(ptr.get())` `Y` . 여기서는 `typename std::shared_ptr<T>::element_type` 입니다. `reinterpret_cast<T*>((U*)nullptr)`가 제대로 구성 되지 않은 경우 동작은 정의 되지 않습니다.

Lvalue 참조를 사용 하는 템플릿 함수는 c + + 17의 새로운 기능입니다. Rvalue 참조를 사용 하는 템플릿 함수는 c + + 20의 새로운 기능입니다.

## <a name="return_temporary_buffer"></a><a name="return_temporary_buffer"></a> return_temporary_buffer

`get_temporary_buffer` 템플릿 함수를 사용하여 할당된 임시 메모리를 취소합니다.

```cpp
template <class T>
void return_temporary_buffer(
    T* buffer);
```

### <a name="parameters"></a>매개 변수

*버퍼*\
할당을 취소할 메모리에 대한 포인터입니다.

### <a name="remarks"></a>설명

임시 메모리에 대해서만이 함수를 사용 합니다.

### <a name="example"></a>예제

```cpp
// memory_ret_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
         << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
         << " could store is given by: resultPair.second = "
         << resultPair.second << "." << endl;

    int* tempBuffer = resultPair.first;

    // Deallocates memory allocated with get_temporary_buffer
    return_temporary_buffer( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a><a name="static_pointer_cast"></a> static_pointer_cast

[Shared_ptr](shared-ptr-class.md)에 대 한 정적 캐스팅입니다.

```cpp
template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>매개 변수

*트*\
반환된 공유 포인터에 의해 제어되는 형식입니다.

*다른*\
인수 공유 포인터에 의해 제어되는 형식입니다.

*sp-2*\
인수 공유 포인터입니다.

### <a name="remarks"></a>설명

`shared_ptr` *Sp* 가 빈 개체인 경우 템플릿 함수는 빈 개체를 반환 하 고, `shared_ptr` 그렇지 않은 경우 `shared_ptr<T>` *sp* 에서 소유 하는 리소스를 소유 하는 개체를 반환 합니다. `static_cast<T*>(sp.get())` 식이 유효해야 합니다.

### <a name="example"></a>예제

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::static_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="swap"></a><a name="swap"></a> 스왑을

두 [shared_ptr](shared-ptr-class.md), [unique_ptr](unique-ptr-class.md)또는 [weak_ptr](weak-ptr-class.md) 개체를 교환 합니다.

```cpp
template <class T>
void swap(
    shared_ptr<T>& left,
    shared_ptr<T>& right) noexcept;

template <class T, class Deleter>
void swap(
    unique_ptr<T, Deleter>& left,
    unique_ptr<T, Deleter>& right) noexcept;

template <class T>
void swap(
    weak_ptr<T>& left,
    weak_ptr<T>& right) noexcept;

```

### <a name="parameters"></a>매개 변수

*트*\
인수 포인터에 의해 제어되는 형식입니다.

*Deleter*\
고유 포인터 형식의 deleter입니다.

*비어*\
왼쪽 포인터입니다.

*오른쪽*\
오른쪽 포인터입니다.

### <a name="remarks"></a>설명

템플릿 함수는 `left.swap(right)`을 호출합니다.

### <a name="example"></a>예제

```cpp
// std__memory__swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5

*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="undeclare_no_pointers"></a><a name="undeclare_no_pointers"></a> undeclare_no_pointers

기본 주소 포인터와 블록 크기로 정의된 메모리 블록에 있는 문자는 이제 추적이 가능한 포인터를 포함할 수 있음을 가비지 수집기에 알립니다.

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>매개 변수

*ptr*\
[Declare_no_pointers](#declare_no_pointers)사용 하 여 이전에 표시 된 메모리 주소에 대 한 포인터입니다.

*크기가*\
메모리 범위의 바이트 수입니다. 이 값은 호출에 사용 된 수와 같아야 합니다 `declare_no_pointers` .

### <a name="remarks"></a>설명

함수는 주소 범위에 `[ptr, ptr + size)` 추적 가능한 포인터가 포함 될 수 있음을 가비지 수집기에 알립니다.

## <a name="undeclare_reachable"></a><a name="undeclare_reachable"></a> undeclare_reachable

지정 된 메모리 위치에 대 한 연결 가능성 선언을 취소 합니다.

```cpp
template <class T>
T *undeclare_reachable(
    T* ptr);
```

### <a name="parameters"></a>매개 변수

*ptr*\
[Declare_reachable](#declare_reachable)사용 하 여 이전에 표시 된 메모리 주소에 대 한 포인터입니다.

### <a name="remarks"></a>설명

*Ptr* 이이 아닌 경우 **`nullptr`** 함수는 *ptr* 에 더 이상 연결할 수 없다는 것을 가비지 수집기에 알립니다. *Ptr* 과 동일한 것을 비교 하는 안전 하 게 파생 된 포인터를 반환 합니다.

## <a name="uninitialized_copy"></a><a name="uninitialized_copy"></a> uninitialized_copy

지정된 소스 범위에서 초기화되지 않은 대상 범위로 개체를 복사합니다.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>매개 변수

*policy*\
사용할 실행 정책입니다.

*기본*\
소스 범위에 있는 첫 번째 요소를 주소 지정하는 입력 반복기입니다.

*최신*\
소스 범위에 있는 마지막 요소를 주소 지정하는 입력 반복기입니다.

*dest*\
대상 범위에 있는 첫 번째 요소를 주소 지정하는 정방향 반복기입니다.

### <a name="return-value"></a>반환 값

소스 범위가 비어 있지 않은 경우 대상 범위를 벗어난 첫 번째 위치를 주소 지정 하는 전방 반복기입니다.

### <a name="remarks"></a>설명

이 알고리즘을 사용하면 개체 생성에서 메모리 할당을 분리할 수 있습니다.

템플릿 함수는 다음을 효과적으로 실행합니다.

```cpp
while (first != last)
{
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

코드에서 예외를 throw하지 않는 경우 이 경우 생성된 모든 개체가 제거되고 예외가 다시 throw됩니다.

실행 정책을 포함 하는 오버 로드는 c + + 17의 새로운 기능은입니다.

### <a name="example"></a>예제

```cpp
// memory_uninit_copy.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    Integer(int x) : value(x) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    cout << "The initialized Array contains " << N << " elements: ";
    for (int i = 0; i < N; i++)
    {
        cout << " " << Array[i];
    }
    cout << endl;

    Integer* ArrayPtr = (Integer*)malloc(N * sizeof(int));
    Integer* LArrayPtr = uninitialized_copy(
        Array, Array + N, ArrayPtr);  // C4996

    cout << "Address of position after the last element in the array is: "
        << &Array[0] + N << endl;
    cout << "The iterator returned by uninitialized_copy addresses: "
        << (void*)LArrayPtr << endl;
    cout << "The address just beyond the last copied element is: "
        << (void*)(ArrayPtr + N) << endl;

    if ((&Array[0] + N) == (void*)LArrayPtr)
        cout << "The return value is an iterator "
        << "pointing just beyond the original array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the original array." << endl;

    if ((void*)LArrayPtr == (void*)(ArrayPtr + N))
        cout << "The return value is an iterator "
        << "pointing just beyond the copied array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the copied array." << endl;

    free(ArrayPtr);

    cout << "Note that the exact addresses returned will vary\n"
        << "with the memory allocation in individual computers."
        << endl;
}
```

## <a name="uninitialized_copy_n"></a><a name="uninitialized_copy_n"></a> uninitialized_copy_n

입력 반복기에서 지정된 수의 요소의 복사본을 만듭니다. 복사본은 정방향 반복기에 배치됩니다.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>매개 변수

*policy*\
사용할 실행 정책입니다.

*기본*\
복사할 개체를 참조하는 입력 반복기입니다.

*수*\
개체를 반복할 횟수를 지정하는 부호 있는 또는 부호 없는 정수 형식입니다.

*dest*\
새 복사본의 위치를 참조하는 정방향 반복기입니다.

### <a name="return-value"></a>반환 값

대상을 벗어나는 첫 번째 위치를 주소 지정하는 정방향 반복기입니다. 소스 범위가 비어 있는 경우 반복기는 *먼저* 주소를 처리 합니다.

### <a name="remarks"></a>설명

템플릿 함수는 다음 코드를 효과적으로 실행 합니다.

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

코드에서 예외를 throw하지 않는 경우 이 경우 생성된 모든 개체가 제거되고 예외가 다시 throw됩니다.

실행 정책을 포함 하는 오버 로드는 c + + 17의 새로운 기능은입니다.

## <a name="uninitialized_default_construct"></a><a name="uninitialized_default_construct"></a> uninitialized_default_construct

지정 된 범위에서 반복기의 개체를 기본적으로 생성 `value_type` 합니다.

```cpp
template <class ForwardIterator>
void uninitialized_default_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_default_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>매개 변수

*policy*\
사용할 실행 정책입니다.

*기본*\
생성할 범위의 첫 번째 요소를 주소 지정 하는 반복기입니다.

*최신*\
생성할 범위에서 마지막 요소 하나 다음의 주소를 지정 하는 반복기입니다.

### <a name="remarks"></a>설명

실행 정책이 없는 버전은 다음과 같이 효과적입니다.

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
```

예외가 throw 되는 경우 이전에 생성 된 개체는 지정 되지 않은 순서로 제거 됩니다.

실행 정책이 지정 된 버전은 동일한 결과를 갖지만 지정 된 *정책* 에 따라 실행 됩니다.

이러한 함수는 c + + 17의 새로운 기능입니다.

## <a name="uninitialized_default_construct_n"></a><a name="uninitialized_default_construct_n"></a> uninitialized_default_construct_n

기본값은 `value_type` 지정 된 위치에서 시작 하 여 반복기의 지정 된 수의 개체를 생성 합니다.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>매개 변수

*policy*\
사용할 실행 정책입니다.

*기본*\
생성할 대상 범위에서 첫 번째 요소를 주소 지정 하는 반복기입니다.

*수*\
생성할 대상 범위에 있는 요소 수입니다.

### <a name="return-value"></a>반환 값

소스 범위가 비어 있지 않은 경우 대상 범위를 벗어난 첫 번째 위치를 주소 지정 하는 전방 반복기입니다.

### <a name="remarks"></a>설명

실행 정책이 없는 버전은 다음과 같이 효과적입니다.

```cpp
for (; count>0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
return first;
```

예외가 throw 되는 경우 이전에 생성 된 개체는 지정 되지 않은 순서로 제거 됩니다.

실행 정책이 지정 된 버전은 동일한 결과를 갖지만 지정 된 *정책* 에 따라 실행 됩니다.

이러한 함수는 c + + 17의 새로운 기능입니다.

## <a name="uninitialized_fill"></a><a name="uninitialized_fill"></a> uninitialized_fill

지정된 값의 개체를 초기화되지 않은 대상 범위로 복사합니다.

```cpp
template <class ForwardIterator, class T>
void uninitialized_fill(
    ForwardIterator first,
    ForwardIterator last,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class T>
void uninitialized_fill(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last,
    const T& value);
```

### <a name="parameters"></a>매개 변수

*policy*\
사용할 실행 정책입니다.

*기본*\
초기화할 대상 범위에 있는 첫 번째 요소의 주소를 지정 하는 전방 반복기입니다.

*최신*\
초기화할 대상 범위에 있는 마지막 요소의 주소를 지정 하는 전방 반복기입니다.

*기본값*\
대상 범위를 초기화하는 데 사용할 값입니다.

### <a name="remarks"></a>설명

이 알고리즘을 사용하면 개체 생성에서 메모리 할당을 분리할 수 있습니다.

템플릿 함수는 다음을 효과적으로 실행합니다.

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (value);
```

코드에서 예외를 throw하지 않는 경우 이 경우 생성된 모든 개체가 제거되고 예외가 다시 throw됩니다.

실행 정책을 포함 하는 오버 로드는 c + + 17의 새로운 기능은입니다.

### <a name="example"></a>예제

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value ( 25 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill( Array, Array + N, value );
    cout << "The initialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        {
            cout << Array[ i ].get() << " ";
        }
    cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a><a name="uninitialized_fill_n"></a> uninitialized_fill_n

지정 된 값의 개체를 초기화 되지 않은 대상 범위의 지정 된 수의 요소에 복사 합니다.

```cpp
template <class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ForwardIterator first,
    Size count,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count,
    const T& value);
```

### <a name="parameters"></a>매개 변수

*policy*\
사용할 실행 정책입니다.

*기본*\
초기화할 대상 범위에 있는 첫 번째 요소의 주소를 지정 하는 전방 반복기입니다.

*수*\
초기화할 요소의 수입니다.

*기본값*\
대상 범위를 초기화 하는 데 사용할 값입니다.

### <a name="remarks"></a>설명

이 알고리즘을 사용하면 개체 생성에서 메모리 할당을 분리할 수 있습니다.

템플릿 함수는 다음을 효과적으로 실행합니다.

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(value);
return first;
```

코드에서 예외를 throw하지 않는 경우 이 경우 생성된 모든 개체가 제거되고 예외가 다시 throw됩니다.

실행 정책을 포함 하는 오버 로드는 c + + 17의 새로운 기능은입니다.

### <a name="example"></a>예제

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value( 60 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill_n( Array, N, value );  // C4996
    cout << "The uninitialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        cout << Array[ i ].get() <<  " ";
}
```

## <a name="uninitialized_move"></a><a name="uninitialized_move"></a> uninitialized_move

소스 범위에서 초기화 되지 않은 대상 메모리 영역으로 요소를 이동 합니다.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>매개 변수

*policy*\
사용할 실행 정책입니다.

*기본*\
이동할 소스 범위에서 첫 번째 요소를 주소 지정 하는 입력 반복기입니다.

*최신*\
이동할 소스 범위에서 마지막 요소 하나 다음의 주소를 지정 하는 입력 반복기입니다.

*dest*\
대상 범위의 시작 부분입니다.

### <a name="remarks"></a>설명

실행 정책이 없는 버전은 다음과 같이 효과적입니다.

```cpp
for (; first != last; (void)++dest, ++first)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return dest;
```

예외가 throw 되 면 소스 범위의 일부 개체가 올바르지만 지정 되지 않은 상태로 남아 있을 수 있습니다. 이전에 생성 된 개체는 지정 되지 않은 순서로 제거 됩니다.

실행 정책이 지정 된 버전은 동일한 결과를 갖지만 지정 된 *정책* 에 따라 실행 됩니다.

이러한 함수는 c + + 17의 새로운 기능입니다.

## <a name="uninitialized_move_n"></a><a name="uninitialized_move_n"></a> uninitialized_move_n

소스 범위에서 초기화 되지 않은 대상 메모리 영역으로 지정 된 수의 요소를 이동 합니다.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>매개 변수

*policy*\
사용할 실행 정책입니다.

*기본*\
이동할 소스 범위에서 첫 번째 요소를 주소 지정 하는 입력 반복기입니다.

*수*\
이동할 소스 범위의 요소 수입니다.

*dest*\
대상 범위의 시작 부분입니다.

### <a name="remarks"></a>설명

실행 정책이 없는 버전은 다음과 같이 효과적입니다.

```cpp
for (; count > 0; ++dest, (void) ++first, --count)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return {first, dest};
```

예외가 throw 되 면 소스 범위의 일부 개체가 올바르지만 지정 되지 않은 상태로 남아 있을 수 있습니다. 이전에 생성 된 개체는 지정 되지 않은 순서로 제거 됩니다.

실행 정책이 지정 된 버전은 동일한 결과를 갖지만 지정 된 *정책* 에 따라 실행 됩니다.

이러한 함수는 c + + 17의 새로운 기능입니다.

## <a name="uninitialized_value_construct"></a><a name="uninitialized_value_construct"></a> uninitialized_value_construct

지정 된 범위에서 반복기의 개체 `value_type` 를 값 초기화로 생성 합니다.

```cpp
template <class ForwardIterator>
void uninitialized_value_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_value_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>매개 변수

*policy*\
사용할 실행 정책입니다.

*기본*\
값 구문에 대 한 범위에 있는 첫 번째 요소의 주소를 지정 하는 반복기입니다.

*최신*\
값 구문에 대 한 범위에서 마지막 요소 하나 다음의 주소를 지정 하는 반복기입니다.

### <a name="remarks"></a>설명

실행 정책이 없는 버전은 다음과 같이 효과적입니다.

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
```

예외가 throw 되는 경우 이전에 생성 된 개체는 지정 되지 않은 순서로 제거 됩니다.

실행 정책이 지정 된 버전은 동일한 결과를 갖지만 지정 된 *정책* 에 따라 실행 됩니다.

메모리 할당 오류가 발생 하면 `std::bad_alloc` 예외가 throw 됩니다.

이러한 함수는 c + + 17의 새로운 기능입니다.

## <a name="uninitialized_value_construct_n"></a><a name="uninitialized_value_construct_n"></a> uninitialized_value_construct_n

`value_type`지정 된 위치에서 시작 하 여 값을 초기화 하 여 반복기의 지정 된 수의 개체를 생성 합니다.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>매개 변수

*policy*\
사용할 실행 정책입니다.

*기본*\
생성할 대상 범위에서 첫 번째 요소를 주소 지정 하는 반복기입니다.

*수*\
생성할 대상 범위에 있는 요소 수입니다.

### <a name="remarks"></a>설명

실행 정책이 없는 버전은 다음과 같이 효과적입니다.

```cpp
for (; count > 0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
return first;
```

예외가 throw 되는 경우 이전에 생성 된 개체는 지정 되지 않은 순서로 제거 됩니다.

실행 정책이 지정 된 버전은 동일한 결과를 갖지만 지정 된 *정책* 에 따라 실행 됩니다.

메모리 할당 오류가 발생 하면 `std::bad_alloc` 예외가 throw 됩니다.

이러한 함수는 c + + 17의 새로운 기능입니다.

## <a name="uses_allocator_v"></a><a name="uses_allocator_v"></a> uses_allocator_v

템플릿 값에 액세스 하는 도우미 변수 템플릿입니다 `uses_allocator` .

```cpp
template <class T, class Alloc>
inline constexpr bool uses_allocator_v = uses_allocator<T, Alloc>::value;
```

## <a name="see-also"></a>참고 항목

[\<memory>](memory.md)
