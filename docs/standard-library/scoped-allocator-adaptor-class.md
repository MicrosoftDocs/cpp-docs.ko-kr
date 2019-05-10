---
title: scoped_allocator_adaptor 클래스
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor::rebind Struct
- scoped_allocator/std::scoped_allocator_adaptor::allocate
- scoped_allocator/std::scoped_allocator_adaptor::construct
- scoped_allocator/std::scoped_allocator_adaptor::deallocate
- scoped_allocator/std::scoped_allocator_adaptor::destroy
- scoped_allocator/std::scoped_allocator_adaptor::inner_allocator
- scoped_allocator/std::scoped_allocator_adaptor::max_size
- scoped_allocator/std::scoped_allocator_adaptor::outer_allocator
- scoped_allocator/std::scoped_allocator_adaptor::select_on_container_copy_construction
helpviewer_keywords:
- std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor::allocate
- std::scoped_allocator_adaptor::construct
- std::scoped_allocator_adaptor::deallocate
- std::scoped_allocator_adaptor::destroy
- std::scoped_allocator_adaptor::inner_allocator
- std::scoped_allocator_adaptor::max_size
- std::scoped_allocator_adaptor::outer_allocator
- std::scoped_allocator_adaptor::select_on_container_copy_construction
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
ms.openlocfilehash: c02f5171fac862b6f79e194f5940b0adeb2e93e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348213"
---
# <a name="scopedallocatoradaptor-class"></a>scoped_allocator_adaptor 클래스

할당자의 중첩을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>설명

템플릿 클래스는 할당자 하나 이상의 중첩을 캡슐화합니다. 이러한 각 클래스에는 `outer_allocator_type` 형식의 가장 바깥쪽 할당자(`Outer`와 동일한 의미)가 있습니다. 이 할당자는 `scoped_allocator_adaptor` 개체의 공용 기준입니다. `Outer`는 컨테이너가 사용할 메모리를 할당하는 데 사용됩니다. `outer_allocator`를 호출하여 이 할당자 기준 개체에 대한 참조를 가져올 수 있습니다.

중첩의 나머지 부분 형식은 `inner_allocator_type`입니다. 내부 할당자를 사용하여 컨테이너 내의 요소에 대해 메모리를 할당합니다. `inner_allocator`를 호출하여 이 형식의 저장된 개체에 대한 참조를 가져올 수 있습니다. `Inner...`가 비어 있지 않은 경우 `inner_allocator_type`의 형식은 `scoped_allocator_adaptor<Inner...>`이며 `inner_allocator`는 구성원 개체를 지정합니다. 그렇지 않으면 `inner_allocator_type`의 형식은 `scoped_allocator_adaptor<Outer>`이며 `inner_allocator`는 전체 개체를 지정합니다.

중첩은 임의의 깊이가 지정된 것처럼 작동하며 필요에 따라 가장 안쪽의 캡슐화된 할당자를 복제합니다.

표시되는 인터페이스의 일부분이 아닌 다양한 개념을 통해 이 템플릿 클래스의 동작을 설명할 수 있습니다. *가장 바깥쪽 할당자*는 construct 및 destroy 메서드에 대한 모든 호출을 중재합니다. 이 할당자는 실제로는 재귀 함수 `OUTERMOST(X)`에 의해 정의되며, 여기서 `OUTERMOST(X)`는 다음 중 하나입니다.

- `X.outer_allocator()`의 형식이 올바르면 `OUTERMOST(X)`는 `OUTERMOST(X.outer_allocator())`입니다.

- 그렇지 않으면 `OUTERMOST(X)`가 `X`입니다.

다음의 세 가지 형식이 표시를 위해 정의됩니다.

|형식|설명|
|----------|-----------------|
|`Outermost`|`OUTERMOST(*this)`의 형식입니다.|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>생성자

|이름|설명|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|`scoped_allocator_adaptor` 개체를 생성합니다.|

### <a name="typedefs"></a>형식 정의

|이름|설명|
|----------|-----------------|
|`const_pointer`|이 형식은 `Outer` 할당자와 연결된 `const_pointer`과 동일한 의미입니다.|
|`const_void_pointer`|이 형식은 `Outer` 할당자와 연결된 `const_void_pointer`와 동일한 의미입니다.|
|`difference_type`|이 형식은 `Outer` 할당자와 연결된 `difference_type`과 동일한 의미입니다.|
|`inner_allocator_type`|이 형식은 중첩된 어댑터 `scoped_allocator_adaptor<Inner...>`의 형식과 동일한 의미니다.|
|`outer_allocator_type`|이 형식은 기본 할당자 `Outer`의 형식과 동일한 의미입니다.|
|`pointer`|이 형식은 `Outer` 할당자와 연결된 `pointer`와 동일한 의미입니다.|
|`propagate_on_container_copy_assignment`|`Outer_traits::propagate_on_container_copy_assignment`가 true이거나 `inner_allocator_type::propagate_on_container_copy_assignment`가 true여야 형식은 true입니다.|
|`propagate_on_container_move_assignment`|`Outer_traits::propagate_on_container_move_assignment`이 true이거나 `inner_allocator_type::propagate_on_container_move_assignment`이 true여야 형식은 true입니다.|
|`propagate_on_container_swap`|`Outer_traits::propagate_on_container_swap`이 true이거나 `inner_allocator_type::propagate_on_container_swap`이 true여야 형식은 true입니다.|
|`size_type`|이 형식은 `Outer` 할당자와 연결된 `size_type`과 동일한 의미입니다.|
|`value_type`|이 형식은 `Outer` 할당자와 연결된 `value_type`과 동일한 의미입니다.|
|`void_pointer`|이 형식은 `Outer` 할당자와 연결된 `void_pointer`과 동일한 의미입니다.|

### <a name="structs"></a>구조체

|이름|설명|
|----------|-----------------|
|[scoped_allocator_adaptor::rebind 구조체](#rebind_struct)|`Outer::rebind\<Other>::other` 형식을 `scoped_allocator_adaptor\<Other, Inner...>`와 동일한 의미로 정의합니다.|

### <a name="methods"></a>메서드

|이름|설명|
|----------|-----------------|
|[allocate](#allocate)|`Outer` 할당자를 사용하여 메모리를 할당합니다.|
|[construct](#construct)|개체를 생성합니다.|
|[deallocate](#deallocate)|외부 할당자를 사용하여 개체의 할당을 취소합니다.|
|[destroy](#destroy)|지정된 개체를 제거합니다.|
|[inner_allocator](#inner_allocator)|`inner_allocator_type` 형식의 저장된 개체에 대한 참조를 검색합니다.|
|[max_size](#max_size)|외부 할당자를 통해 할당할 수 있는 개체의 최대 수를 결정합니다.|
|[outer_allocator](#outer_allocator)|`outer_allocator_type` 형식의 저장된 개체에 대한 참조를 검색합니다.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|해당하는 각 할당자에 대해 `select_on_container_copy_construction`을 호출하여 초기화되는 저장된 각각의 allocator 개체를 포함하는 새 `scoped_allocator_adaptor` 개체를 만듭니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<scoped_allocator>

**네임스페이스:** std

## <a name="allocate"></a>  scoped_allocator_adaptor::allocate

`Outer` 할당자를 사용하여 메모리를 할당합니다.

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>매개 변수

*count*<br/>
충분한 스토리지를 할당해야 할 요소의 수입니다.

*hint*<br/>
요청 이전에 할당된 개체의 주소를 찾아서 할당자 개체를 지원할 수 있는 포인터입니다.

### <a name="return-value"></a>반환 값

첫 번째 구성원 함수는 `Outer_traits::allocate(outer_allocator(), count)`를 반환합니다. 두 번째 구성원 함수는 `Outer_traits::allocate(outer_allocator(), count, hint)`를 반환합니다.

## <a name="construct"></a>  scoped_allocator_adaptor::construct

개체를 생성합니다.

```cpp
template <class Ty, class... Atypes>
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,
    tuple<Atypes1&&...>
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr,
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```

### <a name="parameters"></a>매개 변수

*ptr*<br/>
개체를 생성할 메모리 위치에 대한 포인터입니다.

*args*<br/>
인수 목록입니다.

*first*<br/>
쌍에 포함된 첫 번째 형식의 개체입니다.

*second*<br/>
쌍에 포함된 두 번째 형식의 개체입니다.

*right*<br/>
이동하거나 복사할 기존 개체입니다.

### <a name="remarks"></a>설명

개체를 생성 하는 첫 번째 메서드인 *ptr* 를 호출 하 여 `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`여기서 `xargs...` 다음 중 하나입니다.

- `uses_allocator<Ty, inner_allocator_type>`이 false이면 `xargs...`는 `args...`입니다.

- `uses_allocator<Ty, inner_allocator_type>`이 true이고 `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>`가 true이면 `xargs...`는 `allocator_arg, inner_allocator(), args...`입니다.

- `uses_allocator<Ty, inner_allocator_type>`이 true이고 `is_constructible<Ty, args..., inner_allocator()>`가 true이면 `xargs...`는 `args..., inner_allocator()`입니다.

두 번째 메서드는에 있는 pair 개체를 생성 *ptr* 호출 하 여 `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`여기서 `xargs...` 는 `first...` 위의 목록과 같이 수정 하 고 `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`여기서 `xargs...` 는 `second...` 수정 위의 목록입니다.

세 번째 메서드는 `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`와 동일하게 동작합니다.

네 번째 메서드는 `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`와 동일하게 동작합니다.

다섯 번째 메서드는 `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`와 동일하게 동작합니다.

여섯 번째 메서드는 `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`와 동일하게 동작합니다.

## <a name="deallocate"></a>  scoped_allocator_adaptor::deallocate

외부 할당자를 사용하여 개체의 할당을 취소합니다.

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>매개 변수

*ptr*<br/>
할당을 취소할 개체의 시작 위치에 대한 포인터입니다.

*count*<br/>
할당을 취소할 개체의 수입니다.

## <a name="destroy"></a>  scoped_allocator_adaptor::destroy

지정된 개체를 제거합니다.

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>매개 변수

*ptr*<br/>
제거할 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="inner_allocator"></a>  scoped_allocator_adaptor::inner_allocator

`inner_allocator_type` 형식의 저장된 개체에 대한 참조를 검색합니다.

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>반환 값

`inner_allocator_type` 형식의 저장된 개체에 대한 참조입니다.

## <a name="max_size"></a>  scoped_allocator_adaptor::max_size

외부 할당자를 통해 할당할 수 있는 개체의 최대 수를 결정합니다.

```cpp
size_type max_size();
```

### <a name="return-value"></a>반환 값

`Outer_traits::max_size(outer_allocator())`

## <a name="outer_allocator"></a>  scoped_allocator_adaptor::outer_allocator

`outer_allocator_type` 형식의 저장된 개체에 대한 참조를 검색합니다.

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>반환 값

`outer_allocator_type` 형식의 저장된 개체에 대한 참조입니다.

## <a name="rebind_struct"></a>  scoped_allocator_adaptor::rebind 구조체

`Outer::rebind\<Other>::other` 형식을 `scoped_allocator_adaptor\<Other, Inner...>`와 동일한 의미로 정의합니다.

구조체 rebind {형식 정의 other_traits:: rebind\<기타 > Other_alloc; typedef scoped_allocator_adaptor\<Other_alloc, 내부... >. };

## <a name="scoped_allocator_adaptor"></a>  scoped_allocator_adaptor::scoped_allocator_adaptor 생성자

`scoped_allocator_adaptor` 개체를 생성합니다.

```cpp
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(Outer2&& al,
    const Inner&... rest) noexcept;
```

### <a name="parameters"></a>매개 변수

*right*<br/>
기존 `scoped_allocator_adaptor`입니다.

*al*<br/>
외부 할당자로 사용할 기존 할당자입니다.

*rest*<br/>
내부 할당자로 사용할 할당자의 목록입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 기본적으로 저장된 allocator 개체를 생성합니다. 해당 개체에서 저장 된 할당자 개체를 생성 하는 다음 3 개 생성자의 각 *오른쪽*합니다. 마지막 생성자는 인수 목록의 해당 인수에서 저장된 allocator 개체를 생성합니다.

## <a name="select_on_container_copy_construction"></a>  scoped_allocator_adaptor::select_on_container_copy_construction

해당하는 각 할당자에 대해 `select_on_container_copy_construction`을 호출하여 초기화되는 저장된 각각의 allocator 개체를 포함하는 새 `scoped_allocator_adaptor` 개체를 만듭니다.

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>반환 값

이 메서드는 실제로는 `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`을 반환합니다. 결과 새로운 `scoped_allocator_adaptor` 를 호출 하 여 초기화 된 각 저장 된 할당자 개체를 사용 하 여 개체 `al.select_on_container_copy_construction()` 해당 하는 할당자에 대 한 *al*합니다.

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
