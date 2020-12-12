---
description: Allocator_traits 클래스에 대해 자세히 알아보세요.
title: allocator_traits 클래스
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator_traits
- memory/std::allocator_traits::propagate_on_container_move_assignment
- memory/std::allocator_traits::const_pointer
- memory/std::allocator_traits::propagate_on_container_swap
- memory/std::allocator_traits::propagate_on_container_copy_assignment
- memory/std::allocator_traits::difference_type
- memory/std::allocator_traits::allocator_type
- memory/std::allocator_traits::value_type
- memory/std::allocator_traits::pointer
- memory/std::allocator_traits::size_type
- memory/std::allocator_traits::const_void_pointer
- memory/std::allocator_traits::void_pointer
- memory/std::allocator_traits::allocate
- memory/std::allocator_traits::construct
- memory/std::allocator_traits::deallocate
- memory/std::allocator_traits::destroy
- memory/std::allocator_traits::max_size
- memory/std::allocator_traits::select_on_container_copy_construction
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
helpviewer_keywords:
- std::allocator_traits [C++]
- std::allocator_traits [C++], propagate_on_container_move_assignment
- std::allocator_traits [C++], const_pointer
- std::allocator_traits [C++], propagate_on_container_swap
- std::allocator_traits [C++], propagate_on_container_copy_assignment
- std::allocator_traits [C++], difference_type
- std::allocator_traits [C++], allocator_type
- std::allocator_traits [C++], value_type
- std::allocator_traits [C++], pointer
- std::allocator_traits [C++], size_type
- std::allocator_traits [C++], const_void_pointer
- std::allocator_traits [C++], void_pointer
- std::allocator_traits [C++], allocate
- std::allocator_traits [C++], construct
- std::allocator_traits [C++], deallocate
- std::allocator_traits [C++], destroy
- std::allocator_traits [C++], max_size
- std::allocator_traits [C++], select_on_container_copy_construction
ms.openlocfilehash: d60658c5f8cf6217dff7a846f0e5cbae42e6a565
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163563"
---
# <a name="allocator_traits-class"></a>allocator_traits 클래스

클래스 템플릿은 *할당자 형식을* 보완 하는 개체를 설명 합니다. 할당자 형식은 할당된 스토리지를 관리하는 데 사용되는 할당자 개체를 설명하는 형식입니다. 특히 할당자 형식 `Alloc`에 대해서는 할당자를 사용할 수 있는 컨테이너에 필요한 모든 정보를 확인하기 위해 `allocator_traits<Alloc>`를 사용할 수 있습니다. 자세한 내용은 기본 [allocator 클래스](allocator-class.md)를 참조하세요.

## <a name="syntax"></a>구문

```cpp
template <class Alloc>
    class allocator_traits;
```

## <a name="members"></a>멤버

### <a name="typedefs"></a>Typedefs

|Name|설명|
|-|-|
|`allocator_type`|이 형식은 템플릿 매개 변수 `Alloc`의 동의어입니다.|
|`const_pointer`|잘 구성된 형식인 경우 이 형식은 `Alloc::const_pointer`이고, 아닌 경우 `pointer_traits<pointer>::rebind<const value_type>`입니다.|
|`const_void_pointer`|잘 구성된 형식인 경우 이 형식은 `Alloc::const_void_pointer`이고, 아닌 경우 `pointer_traits<pointer>::rebind<const void>`입니다.|
|`difference_type`|잘 구성된 형식인 경우 이 형식은 `Alloc::difference_type`이고, 아닌 경우 `pointer_traits<pointer>::difference_type`입니다.|
|`pointer`|잘 구성된 형식인 경우 이 형식은 `Alloc::pointer`이고, 아닌 경우 `value_type *`입니다.|
|`propagate_on_container_copy_assignment`|잘 구성된 형식인 경우 이 형식은 `Alloc::propagate_on_container_copy_assignment`이고, 아닌 경우 `false_type`입니다.|
|`propagate_on_container_move_assignment`|잘 구성된 형식인 경우 이 형식은 `Alloc::propagate_on_container_move_assignment`이고, 아닌 경우 `false_type`입니다. 형식이 true이면, 할당자를 사용할 수 있는 컨테이너는 이동 할당 시 저장된 할당자를 복사합니다.|
|`propagate_on_container_swap`|잘 구성된 형식인 경우 이 형식은 `Alloc::propagate_on_container_swap`이고, 아닌 경우 `false_type`입니다. 형식이 true이면, 할당자를 사용할 수 있는 컨테이너는 교환 시 저장된 할당자를 교환합니다.|
|`size_type`|잘 구성된 형식인 경우 이 형식은 `Alloc::size_type`이고, 아닌 경우 `make_unsigned<difference_type>::type`입니다.|
|`value_type`|이 형식은 `Alloc::value_type`의 동의어입니다.|
|`void_pointer`|잘 구성된 형식인 경우 이 형식은 `Alloc::void_pointer`이고, 아닌 경우 `pointer_traits<pointer>::rebind<void>`입니다.|

### <a name="static-methods"></a>정적 메서드

다음 정적 메서드는 지정된 할당자 매개 변수에서 해당 메서드를 호출합니다.

|Name|설명|
|-|-|
|[추가로](#allocate)|지정된 할당자 매개 변수를 사용하여 메모리를 할당하는 정적 메서드입니다.|
|[구축](#construct)|지정된 할당자를 사용하여 개체를 생성하는 정적 메서드입니다.|
|[할당](#deallocate)|지정된 할당자를 사용하여 지정된 수의 개체를 할당 해제하는 정적 메서드입니다.|
|[삭제](#destroy)|지정된 할당자를 사용하여 메모리를 할당 취소하지 않고 개체에서 소멸자를 호출하는 정적 메서드입니다.|
|[max_size](#max_size)|지정된 할당자를 사용하여 할당 가능한 개체의 최대 수를 결정하는 정적 메서드입니다.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|지정된 할당자에서 `select_on_container_copy_construction`을 호출하는 정적 메서드입니다.|

### <a name="allocate"></a><a name="allocate"></a> 추가로

지정된 할당자 매개 변수를 사용하여 메모리를 할당하는 정적 메서드입니다.

```cpp
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```

#### <a name="parameters"></a>매개 변수

*항상*\
할당자 개체입니다.

*수*\
할당할 요소의 수입니다.

*힌트*\
요청 이전에 할당된 개체의 주소를 찾음으로써 스토리지에 대한 요청을 충족하여 할당자 개체를 지원할 수 있는 `const_pointer`입니다. Null 포인터는 힌트 없음으로 처리됩니다.

#### <a name="return-value"></a>반환 값

각 메서드는 할당된 개체에 대한 포인터를 반환합니다.

첫 번째 정적 메서드는 `al.allocate(count)`를 반환합니다.

해당 식이 잘 구성되어 있는 경우 두 번째 메서드는 `al.allocate(count, hint)`를 반환하고, 아닌 경우 `al.allocate(count)`를 반환합니다.

### <a name="construct"></a><a name="construct"></a> 구축

지정된 할당자를 사용하여 개체를 생성하는 정적 메서드입니다.

```cpp
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```

#### <a name="parameters"></a>매개 변수

*항상*\
할당자 개체입니다.

*ptr*\
개체를 생성할 위치에 대한 포인터입니다.

*args*\
개체 생성자에 전달되는 인수 목록입니다.

#### <a name="remarks"></a>설명

해당 식이 잘 구성되어 있는 경우 정적 멤버 함수는 `al.construct(ptr, args...)`를 호출하고, 아닌 경우 `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)`를 평가합니다.

### <a name="deallocate"></a><a name="deallocate"></a> 할당

지정된 할당자를 사용하여 지정된 수의 개체를 할당 해제하는 정적 메서드입니다.

```cpp
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```

#### <a name="parameters"></a>매개 변수

*항상*\
할당자 개체입니다.

*ptr*\
할당을 취소할 개체의 시작 위치에 대한 포인터입니다.

*수*\
할당을 취소할 개체의 수입니다.

#### <a name="remarks"></a>설명

이 메서드는 `al.deallocate(ptr, count)`를 호출합니다.

이 메서드는 아무것도 throw하지 않습니다.

### <a name="destroy"></a><a name="destroy"></a> 삭제

지정된 할당자를 사용하여 메모리를 할당 취소하지 않고 개체에서 소멸자를 호출하는 정적 메서드입니다.

```cpp
template <class Uty>
    static void destroy(Alloc& al, Uty* ptr);
```

#### <a name="parameters"></a>매개 변수

*항상*\
할당자 개체입니다.

*ptr*\
개체의 위치에 대한 포인터입니다.

#### <a name="remarks"></a>설명

해당 식이 잘 구성되어 있는 경우 이 메서드는 `al.destroy(ptr)`를 호출하고, 아닌 경우 `ptr->~Uty()`를 평가합니다.

### <a name="max_size"></a><a name="max_size"></a> max_size

지정된 할당자를 사용하여 할당 가능한 개체의 최대 수를 결정하는 정적 메서드입니다.

```cpp
static size_type max_size(const Alloc& al);
```

#### <a name="parameters"></a>매개 변수

*항상*\
할당자 개체입니다.

#### <a name="remarks"></a>설명

해당 식이 잘 구성되어 있는 경우 이 메서드는 `al.max_size()`를 반환하고, 아닌 경우 `numeric_limits<size_type>::max()`를 반환합니다.

### <a name="select_on_container_copy_construction"></a><a name="select_on_container_copy_construction"></a> select_on_container_copy_construction

지정된 할당자에서 `select_on_container_copy_construction`을 호출하는 정적 메서드입니다.

```cpp
static Alloc select_on_container_copy_construction(const Alloc& al);
```

#### <a name="parameters"></a>매개 변수

*항상*\
할당자 개체입니다.

#### <a name="return-value"></a>반환 값

`al.select_on_container_copy_construction()`형식이 올바른 형식이 면이 메서드는을 반환 하 고 그렇지 않으면 *al* 을 반환 합니다.

#### <a name="remarks"></a>설명

이 메서드는 연결된 컨테이너를 복사하여 생성할 할당자를 지정하는 데 사용됩니다.
