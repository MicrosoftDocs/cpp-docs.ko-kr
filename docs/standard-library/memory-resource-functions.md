---
title: '&lt;memory_resource &gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- memory_resource/std::get_default_resource
- memory_resource/std::new_delete_resource
- memory_resource/std::null_memory_resource
- memory_resource/std::polymorphic_allocator
- memory_resource/std::set_default_resource
helpviewer_keywords:
- std::get_default_resource [C++]
- std::new_delete_resource [C++]
- std::null_memory_resource [C++]
- std::polymorphic_allocator [C++]
- std::set_default_resource [C++]
ms.openlocfilehash: 19d061b75a4f90a5779cad1a131e304623c4adf8
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040589"
---
# <a name="ltmemory_resourcegt-functions"></a>&lt;memory_resource &gt; 함수

## <a name="get_default_resource"></a><a name="get_default"></a> get_default_resource

```cpp
memory_resource* get_default_resource() noexcept;
```

## <a name="new_delete_resource"></a><a name="new_delete"></a> new_delete_resource

```cpp
memory_resource* new_delete_resource() noexcept;
```

## <a name="null_memory_resource"></a><a name="null_memory"></a> null_memory_resource

```cpp
memory_resource* null_memory_resource() noexcept;
```

## <a name="polymorphic_allocator"></a><a name="poly_alloc"></a> polymorphic_allocator

```cpp
template <class Tp>
class polymorphic_allocator {
    memory_resource* memory_rsrc; // exposition only

    public:
    using value_type = Tp;

    polymorphic_allocator() noexcept;
    polymorphic_allocator(memory_resource* r);
    polymorphic_allocator(const polymorphic_allocator& other) = default;
    template <class U>
        polymorphic_allocator(const polymorphic_allocator<U>& other) noexcept;
    polymorphic_allocator&
        operator=(const polymorphic_allocator& rhs) = delete;

    Tp* allocate(size_t n);
    void deallocate(Tp* p, size_t n);
    template <class T, class... Args>
        void construct(T* p, Args&&... args);
    template <class T1, class T2, class... Args1, class... Args2>
        void construct(pair<T1,T2>* p, piecewise_construct_t,
    tuple<Args1...> x, tuple<Args2...> y);
    template <class T1, class T2>
        void construct(pair<T1,T2>* p);
    template <class T1, class T2, class U, class V>
        void construct(pair<T1,T2>* p, U&& x, V&& y);
    template <class T1, class T2, class U, class V>
        void construct(pair<T1,T2>* p, const pair<U, V>& pr);
    template <class T1, class T2, class U, class V>
        void construct(pair<T1,T2>* p, pair<U, V>&& pr);
    template <class T>
        void destroy(T* p);
    polymorphic_allocator select_on_container_copy_construction() const;
    memory_resource* resource() const;
};
```

## <a name="set_default_resource"></a><a name="set_default"></a> set_default_resource

```cpp
memory_resource* set_default_resource(memory_resource* r) noexcept;
```
