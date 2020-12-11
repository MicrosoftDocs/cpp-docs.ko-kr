---
description: '다음에 대 한 자세한 정보: 할당자'
title: Allocators
ms.date: 11/04/2016
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
ms.openlocfilehash: 4001ba007037e50ca3c5d2bea079f313b1c52bc3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163433"
---
# <a name="allocators"></a>Allocators

할당자는 C++ 표준 라이브러리에서 컨테이너에 저장된 요소의 할당 및 할당 취소를 처리하는 데 사용됩니다. std::array를 제외한 모든 C++ 표준 라이브러리 컨테이너에는 `allocator<Type>` 형식의 템플릿 매개 변수가 있습니다. 여기서 `Type`은 컨테이너 요소의 형식을 나타냅니다. 예를 들어 vector 클래스는 다음과 같이 선언됩니다.

```cpp
template <
    class Type,
    class Allocator = allocator<Type>
>
class vector
```

C++ 표준 라이브러리에서는 할당자에 대한 기본 구현을 제공합니다. C++11 이상에서 기본 할당자는 더 작은 인터페이스를 표시하도록 업데이트되고 새 할당자를 *최소 할당자* 라고 합니다. 특히 최소 할당자의 `construct()` 멤버는 성능을 크게 향상할 수 있는 이동 의미 체계를 지원합니다. 대부분 이 기본 할당자로 충분해야 합니다. C++ 11에서 할당자 형식 매개 변수를 사용하는 모든 표준 라이브러리 형식 및 함수는 `std::function`, `shared_ptr, allocate_shared()` 및 `basic_string`을 포함한 최소 할당자 인터페이스를 지원합니다.  기본 할당자에 대한 자세한 내용은 [allocator 클래스](allocator-class.md)를 참조하세요.

## <a name="writing-your-own-allocator-c11"></a>고유한 할당자 작성(C++11)

기본 할당자는 및를 사용 하 여 **`new`** **`delete`** 메모리를 할당 및 할당 취소 합니다. 공유 메모리를 사용하는 등의 다른 메모리 할당 방법을 사용하려면 고유한 할당자를 만들어야 합니다. C++11을 대상으로 지정하고 새 사용자 지정 할당자를 작성해야 할 경우 가능하면 최소 할당자로 설정하세요. 이전 스타일 할당자를 이미 구현했더라도 자동으로 제공되는 더 효율적인 `construct()` 메서드를 사용하기 위해 이전 스타일 할당자를 *최소 할당자* 로 수정하는 것이 좋습니다.

최소 할당자에는 훨씬 더 적은 상용구가 필요하고 최소 할당자를 사용하여 모든 작업을 수행하는 `allocate` 및 `deallocate` 멤버 함수에 포커스를 지정할 수 있습니다. 최소 할당자를 만들 때 아래 예제에 표시된 멤버를 제외한 멤버를 구현하지 마세요.

1. 변환 복사 생성자(예제 참조)

1. operator==

1. operator!=

1. 할당

1. deallocate

제공되는 C++11 기본 `construct()` 멤버는 완벽한 전달을 수행하고 이동 의미 체계를 가능하게 하므로 이전 버전보다 대부분 경우에 훨씬 더 효율적입니다.

> [!WARNING]
> 컴파일 시간에 C++ 표준 라이브러리에서는 allocator_traits 클래스를 사용하여 명시적으로 제공한 멤버를 감지하고 존재하지 않는 모든 멤버에 대한 기본 구현을 제공합니다. 할당자에 대한 allocator_traits의 특수화를 제공하여 이 메커니즘을 방해하지 마세요.

다음 예제에서는 `malloc` 및 `free`를 사용하는 할당자의 최소 구현을 보여 줍니다. 배열 크기가 0보다 작거나 최대 허용 크기보다 클 경우 throw되는 새 예외 형식 `std::bad_array_new_length`의 사용에 주의하세요.

```cpp
#pragma once
#include <stdlib.h> //size_t, malloc, free
#include <new> // bad_alloc, bad_array_new_length
#include <memory>
template <class T>
struct Mallocator
{
    typedef T value_type;
    Mallocator() noexcept {} //default ctor not required by C++ Standard Library

    // A converting copy constructor:
    template<class U> Mallocator(const Mallocator<U>&) noexcept {}
    template<class U> bool operator==(const Mallocator<U>&) const noexcept
    {
        return true;
    }
    template<class U> bool operator!=(const Mallocator<U>&) const noexcept
    {
        return false;
    }
    T* allocate(const size_t n) const;
    void deallocate(T* const p, size_t) const noexcept;
};

template <class T>
T* Mallocator<T>::allocate(const size_t n) const
{
    if (n == 0)
    {
        return nullptr;
    }
    if (n > static_cast<size_t>(-1) / sizeof(T))
    {
        throw std::bad_array_new_length();
    }
    void* const pv = malloc(n * sizeof(T));
    if (!pv) { throw std::bad_alloc(); }
    return static_cast<T*>(pv);
}

template<class T>
void Mallocator<T>::deallocate(T * const p, size_t) const noexcept
{
    free(p);
}
```

## <a name="writing-your-own-allocator-c03"></a>고유한 할당자 작성(C++03)

C++ 03에서 C++ 표준 라이브러리 컨테이너와 함께 사용된 모든 할당자는 다음 형식 정의를 구현해야 합니다.

:::row:::
   :::column:::
      `const_pointer`\
      `const_reference`
   :::column-end:::
   :::column:::
      `difference_type`\
      `pointer`
   :::column-end:::
   :::column:::
      `rebind`\
      `reference`
   :::column-end:::
   :::column:::
      `size_type`\
      `value_type`
   :::column-end:::
:::row-end:::

또한 C++ 표준 라이브러리 컨테이너와 함께 사용된 모든 할당자는 다음 메서드를 구현해야 합니다.

:::row:::
   :::column:::
      생성자
      복사 생성자 \
      소멸자
   :::column-end:::
   :::column:::
      `address`\
      `allocate`\
      `construct`
   :::column-end:::
   :::column:::
      `deallocate`\
      `destroy`\
      `max_size`
   :::column-end:::
   :::column:::
      `operator!=`\
      `operator==`
   :::column-end:::
:::row-end:::

이러한 형식 정의 및 메서드에 대한 자세한 내용은 [allocator 클래스](allocator-class.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리 참조](cpp-standard-library-reference.md)
