---
description: '다음에 대 한 자세한 정보: &lt; 할당자 &gt; 매크로'
title: '&lt;allocators&gt; macros'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
helpviewer_keywords:
- std::ALLOCATOR_DECL [C++]
- std::CACHE_CHUNKLIST [C++]
- std::CACHE_FREELIST [C++]
- std::CACHE_SUBALLOC [C++]
- std::SYNC_DEFAULT [C++]
ms.openlocfilehash: c4866495787cbf502997ca08a06e57ed667f4e9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163524"
---
# <a name="ltallocatorsgt-macros"></a>&lt;allocators&gt; macros

:::row:::
   :::column span="":::
      [`ALLOCATOR_DECL`](#allocator_decl)\
      [`CACHE_CHUNKLIST`](#cache_chunklist)
   :::column-end:::
   :::column span="":::
      [`CACHE_FREELIST`](#cache_freelist)
   :::column-end:::
   :::column span="":::
      [`CACHE_SUBALLOC`](#cache_suballoc)
   :::column-end:::
   :::column span="":::
      [`SYNC_DEFAULT`](#sync_default)
   :::column-end:::
:::row-end:::

## <a name="allocator_decl"></a><a name="allocator_decl"></a> ALLOCATOR_DECL

할당자 클래스 템플릿을 생성 합니다.

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>설명

매크로는 `template <class Type> class name {.....}` `template <> class name<void> {.....}` 동기화 필터 및 형식의 캐시를 사용 하는 할당자 클래스 템플릿을 함께 정의 하는 템플릿 정의와 특수화를 생성 합니다 `sync` `cache` .

rebind를 컴파일할 수 있는 컴파일러의 경우, 결과 템플릿 정의는 다음과 같습니다.

```cpp
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };
```

rebind를 컴파일할 수 없는 컴파일러의 경우, 결과 템플릿 정의는 다음과 같습니다.

```cpp
template <class Type<class name
    : public stdext::allocators::allocator_base<Type,
    sync<stdext::allocators::rts_alloc<cache>>>
{
public:
    name() {}
    template <class Other>
    name(const name<Other>&) {}
    template <class Other>
    name& operator= (const name<Other>&)
    {
        return *this;
    }
};
```

## <a name="cache_chunklist"></a><a name="cache_chunklist"></a> CACHE_CHUNKLIST

`stdext::allocators::cache_chunklist<sizeof(Type)>`을 생성합니다.

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>설명

## <a name="cache_freelist"></a><a name="cache_freelist"></a> CACHE_FREELIST

`stdext::allocators::cache_freelist<sizeof(Type), max>`을 생성합니다.

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>설명

## <a name="cache_suballoc"></a><a name="cache_suballoc"></a> CACHE_SUBALLOC

`stdext::allocators::cache_suballoc<sizeof(Type)>`을 생성합니다.

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>설명

## <a name="sync_default"></a><a name="sync_default"></a> SYNC_DEFAULT

동기화 필터를 생성합니다.

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>설명

컴파일러가 단일 스레드 및 다중 스레드 애플리케이션 컴파일을 모두 지원하는 경우 단일 스레드 애플리케이션에 대해 매크로는 `stdext::allocators::sync_none`을 생성하고, 다른 모든 경우 `stdext::allocators::sync_shared`를 생성합니다.

## <a name="see-also"></a>참고 항목

[\<allocators>](allocators-header.md)
