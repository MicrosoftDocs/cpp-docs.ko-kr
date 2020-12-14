---
description: Forward_list 클래스에 대해 자세히 알아보세요.
title: forward_list 클래스
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::forward_list
- forward_list/std::forward_list::allocator_type
- forward_list/std::forward_list::const_iterator
- forward_list/std::forward_list::const_pointer
- forward_list/std::forward_list::const_reference
- forward_list/std::forward_list::difference_type
- forward_list/std::forward_list::iterator
- forward_list/std::forward_list::pointer
- forward_list/std::forward_list::reference
- forward_list/std::forward_list::size_type
- forward_list/std::forward_list::value_type
- forward_list/std::forward_list::assign
- forward_list/std::forward_list::before_begin
- forward_list/std::forward_list::begin
- forward_list/std::forward_list::cbefore_begin
- forward_list/std::forward_list::cbegin
- forward_list/std::forward_list::cend
- forward_list/std::forward_list::clear
- forward_list/std::forward_list::emplace_after
- forward_list/std::forward_list::emplace_front
- forward_list/std::forward_list::empty
- forward_list/std::forward_list::end
- forward_list/std::forward_list::erase_after
- forward_list/std::forward_list::front
- forward_list/std::forward_list::get_allocator
- forward_list/std::forward_list::insert_after
- forward_list/std::forward_list::max_size
- forward_list/std::forward_list::merge
- forward_list/std::forward_list::pop_front
- forward_list/std::forward_list::push_front
- forward_list/std::forward_list::remove
- forward_list/std::forward_list::remove_if
- forward_list/std::forward_list::resize
- forward_list/std::forward_list::reverse
- forward_list/std::forward_list::sort
- forward_list/std::forward_list::splice_after
- forward_list/std::forward_list::swap
- forward_list/std::forward_list::unique
helpviewer_keywords:
- std::forward_list
- std::forward_list::allocator_type
- std::forward_list::const_iterator
- std::forward_list::const_pointer
- std::forward_list::const_reference
- std::forward_list::difference_type
- std::forward_list::iterator
- std::forward_list::pointer
- std::forward_list::reference
- std::forward_list::size_type
- std::forward_list::value_type
- std::forward_list::assign
- std::forward_list::before_begin
- std::forward_list::begin
- std::forward_list::cbefore_begin
- std::forward_list::cbegin
- std::forward_list::cend
- std::forward_list::clear
- std::forward_list::emplace_after
- std::forward_list::emplace_front
- std::forward_list::empty
- std::forward_list::end
- std::forward_list::erase_after
- std::forward_list::front
- std::forward_list::get_allocator
- std::forward_list::insert_after
- std::forward_list::max_size
- std::forward_list::merge
- std::forward_list::pop_front
- std::forward_list::push_front
- std::forward_list::remove
- std::forward_list::remove_if
- std::forward_list::resize
- std::forward_list::reverse
- std::forward_list::sort
- std::forward_list::splice_after
- std::forward_list::swap
- std::forward_list::unique
ms.openlocfilehash: 3d9cb038123b093f81f5eb4fca49db77885ff1d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232410"
---
# <a name="forward_list-class"></a>forward_list 클래스

다양한 길이의 요소 시퀀스를 제어하는 개체를 설명합니다. 각각 `Type` 형식의 멤버를 포함하는 노드의 단일 연결 목록으로 시퀀스가 저장됩니다.

## <a name="syntax"></a>구문

```cpp
template <class Type,
    class Allocator = allocator<Type>>
class forward_list
```

### <a name="parameters"></a>매개 변수

* \을 입력 합니다.
forward_list에 저장되는 요소 데이터 형식입니다.

*할당자*\
forward_list의 메모리 할당 및 할당 취소에 대한 세부 정보를 캡슐화하는 저장된 할당자 개체입니다. 이 매개 변수는 선택 사항입니다. 기본값은 할당자<`Type`>입니다.

## <a name="remarks"></a>설명

`forward_list`개체는 [할당자 클래스](../standard-library/allocator-class.md) (일반적으로 라고 함)를 기반으로 하는 클래스 *할당자* 의 저장 된 개체를 통해 제어 하는 시퀀스에 대 한 저장소를 할당 하 고 해제 `std::allocator)` 합니다. 자세한 내용은 [할당자](../standard-library/allocators.md)를 참조하세요. 할당자 개체에는 형식의 개체와 동일한 외부 인터페이스가 있어야 합니다 `allocator` .

> [!NOTE]
> 컨테이너 개체를 할당하는 경우 저장된 할당자 개체는 복사되지 않습니다.

`forward_list`를 통해 제어되는 시퀀스의 요소를 지울 경우 반복기, 포인터 및 참조가 무효화될 수도 있습니다. `forward_list`를 통해 제어되는 시퀀스에서 수행되는 삽입 및 스플라이스는 반복기를 무효화하지 않습니다.

제어되는 시퀀스에 대한 추가는 `Type(const  T&)` 생성자를 호출하는 유일한 멤버 함수인 [forward_list::insert_after](#insert_after)를 호출하여 발생할 수 있습니다. `forward_list`는 이동 생성자를 호출할 수도 있습니다. 이러한 식에서 예외가 발생하는 경우 컨테이너 개체는 새 요소를 삽입하지 않고 예외를 다시 발생시킵니다. 따라서 `forward_list` 이러한 예외가 발생 하면 형식의 개체가 알려진 상태로 유지 됩니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[forward_list](#forward_list)|`forward_list` 형식의 개체를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|Name|설명|
|-|-|
|[allocator_type](#allocator_type)|정방향 목록 개체의 할당자 클래스를 나타내는 형식입니다.|
|[const_iterator](#const_iterator)|정방향 목록에 대한 상수 반복기를 제공하는 형식입니다.|
|[const_pointer](#const_pointer)|전방 목록의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .|
|[const_reference](#const_reference)|정방향 목록의 요소에 대한 상수 참조를 제공하는 형식입니다.|
|[difference_type](#difference_type)|반복기가 가리키는 요소 사이의 범위에 있는 정방향 목록의 요소 수를 나타내는 데 사용할 수 있는 부호 있는 정수 형식입니다.|
|[iterator](#iterator)|정방향 목록에 대한 반복기를 제공하는 형식입니다.|
|[놓고](#pointer)|정방향 목록의 요소에 대한 포인터를 제공하는 형식입니다.|
|[reference](#reference)|정방향 목록의 요소에 대한 참조를 제공하는 형식입니다.|
|[size_type](#size_type)|두 요소 사이의 부호가 없는 거리를 나타내는 형식입니다.|
|[value_type](#value_type)|정방향 목록에 저장된 요소의 형식을 나타내는 형식입니다.|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[assign](#assign)|정방향 목록에서 요소를 삭제하고 대상 정방향 목록에서 요소의 새 집합을 복사합니다.|
|[before_begin](#before_begin)|정방향 목록에서 첫 번째 요소 앞의 위치에 주소를 지정하는 반복기를 반환합니다.|
|[시작](#begin)|정방향 목록에서 첫 번째 요소의 주소를 지정하는 반복기를 반환합니다.|
|[cbefore_begin](#cbefore_begin)|정방향 목록에서 첫 번째 요소 앞의 위치에 주소를 지정하는 const 반복기를 반환합니다.|
|[cbegin](#cbegin)|정방향 목록에서 첫 번째 요소의 주소를 지정하는 const 반복기를 반환합니다.|
|[cend](#cend)|정방향 목록에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 const 반복기를 반환합니다.|
|[clear](#clear)|정방향 목록의 모든 요소를 지웁니다.|
|[emplace_after](#emplace_after)|이동 후 지정된 위치 뒤에 새 요소를 생성합니다.|
|[emplace_front](#emplace_front)|생성된 요소를 목록 시작 부분에 추가합니다.|
|[empty](#empty)|정방향 목록이 비어 있는지 테스트합니다.|
|[end](#end)|정방향 목록에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.|
|[erase_after](#erase_after)|정방향 목록의 지정된 위치 뒤에서 요소를 제거합니다.|
|[앞뒤](#front)|정방향 목록의 첫 번째 요소에 대한 참조를 반환합니다.|
|[get_allocator](#get_allocator)|정방향 목록을 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.|
|[insert_after](#insert_after)|정방향 목록의 지정된 위치 뒤에 요소를 추가합니다.|
|[max_size](#max_size)|정방향 목록의 최대 길이를 반환합니다.|
|[결합](#merge)|요소를 인수 목록에서 제거하고 대상 정방향 목록에 삽입한 다음 새로 조합된 요소 집합을 오름차순 또는 기타 지정된 순서로 정렬합니다.|
|[pop_front](#pop_front)|정방향 목록의 시작 부분에 있는 요소를 삭제합니다.|
|[push_front](#push_front)|정방향 목록의 시작 부분에 요소를 추가합니다.|
|[remove](#remove)|정방향 목록에서 지정된 값과 일치하는 요소를 지웁니다.|
|[remove_if](#remove_if)|지정된 조건자를 충족하는 요소를 정방향 목록에서 지웁니다.|
|[조정해](#resize)|정방향 목록의 새 크기를 지정합니다.|
|[되돌립니다](#reverse)|정방향 목록에 요소가 나타나는 순서를 반대로 바꿉니다.|
|[sort](#sort)|오름차순 또는 조건자를 통해 지정된 순서로 요소를 정렬합니다.|
|[splice_after](#splice_after)|노드 간의 연결을 다시 붙입니다.|
|[스왑을](#swap)|두 정방향 목록의 요소를 교환합니다.|
|[unique](#unique)|지정된 테스트를 통과하는 인접 요소를 제거합니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자 =](#op_eq)|정방향 목록의 요소를 다른 정방향 목록의 복사본으로 바꿉니다.|

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

정방향 목록 개체의 할당자 클래스를 나타내는 형식입니다.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>설명

`allocator_type`은 템플릿 매개 변수 Allocator의 동의어입니다.

## <a name="assign"></a><a name="assign"></a> 할당

정방향 목록에서 요소를 삭제하고 대상 정방향 목록에서 요소의 새 집합을 복사합니다.

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign(
    initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>매개 변수

*기본*\
대체 범위의 시작입니다.

*최신*\
대체 범위의 끝입니다.

*수*\
할당할 요소 수입니다.

*짧은*\
각 요소에 할당할 값입니다.

*입력할*\
값의 형식입니다.

*IList*\
복사할 initializer_list입니다.

### <a name="remarks"></a>설명

forward_list가 정수 형식이면 첫 번째 멤버 함수는 `assign((size_type)First, (Type)Last)`와 동일하게 동작합니다. 그렇지 않으면 첫 번째 멤버 함수는로 제어 되는 시퀀스를 **`*this`** `First, Last)` 초기 제어 되는 시퀀스와 겹치지 않아야 하는 sequence [로 바꿉니다.

두 번째 멤버 함수는로 제어 되는 시퀀스를 **`*this`** `Count` 값의 요소 반복으로 바꿉니다 `Val` .

세 번째 멤버 함수는 initializer_list의 요소를 forward_list로 복사합니다.

## <a name="before_begin"></a><a name="before_begin"></a> before_begin

정방향 목록에서 첫 번째 요소 앞의 위치에 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator before_begin() const;
iterator before_begin();
```

### <a name="return-value"></a>반환 값

시퀀스의 첫 번째 요소 바로 앞(또는 빈 시퀀스의 끝 바로 앞)을 가리키는 정방향 반복기입니다.

### <a name="remarks"></a>설명

## <a name="begin"></a><a name="begin"></a> begin

정방향 목록에서 첫 번째 요소의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>반환 값

시퀀스의 첫 번째 요소(또는 빈 시퀀스의 끝 바로 다음)를 가리키는 정방향 반복기입니다.

### <a name="remarks"></a>설명

## <a name="cbefore_begin"></a><a name="cbefore_begin"></a> cbefore_begin

정방향 목록에서 첫 번째 요소 앞의 위치에 주소를 지정하는 const 반복기를 반환합니다.

```cpp
const_iterator cbefore_begin() const;
```

### <a name="return-value"></a>반환 값

시퀀스의 첫 번째 요소 바로 앞(또는 빈 시퀀스의 끝 바로 앞)을 가리키는 정방향 반복기입니다.

### <a name="remarks"></a>설명

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

**`const`** 범위에 있는 첫 번째 요소의 주소를 처리 하는 반복기를 반환 합니다.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>반환 값

**`const`** 범위의 첫 번째 요소 또는 빈 범위의 끝 바로 다음 위치를 가리키는 전방 액세스 반복기입니다 (빈 범위의 경우 `cbegin() == cend()` ).

### <a name="remarks"></a>설명

`cbegin` 반환 값을 사용하여 범위의 요소를 수정할 수 없습니다.

`begin()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container` 및를 지 원하는 수정 가능 (비 **`const`** ) 컨테이너로 가정 `begin()` `cbegin()` 합니다.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> cend

**`const`** 범위에서 마지막 요소 바로 다음 위치의 주소를 가리키는 반복기를 반환 합니다.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>반환 값

범위 끝의 바로 다음을 가리키는 정방향 액세스 반복기입니다.

### <a name="remarks"></a>설명

`cend`는 반복기가 범위 끝을 통과했는지 여부를 테스트하는 데 사용됩니다.

`end()` 멤버 함수 대신 이 멤버 함수를 사용하여 반환 값이 `const_iterator`임을 보장할 수 있습니다. 일반적으로 다음 예제와 같이 [auto](../cpp/auto-cpp.md) 형식 추론 키워드와 함께 사용합니다. 이 예제에서는 `Container` 및를 지 원하는 수정 가능 (비 **`const`** ) 컨테이너로 가정 `end()` `cend()` 합니다.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend`에서 반환한 값은 역참조되지 않아야 합니다.

## <a name="clear"></a><a name="clear"></a> 해제

정방향 목록의 모든 요소를 지웁니다.

```cpp
void clear();
```

### <a name="remarks"></a>설명

이 멤버 함수는 `erase_after(before_begin(), end()).`를 호출합니다.

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

정방향 목록에 대한 상수 반복기를 제공하는 형식입니다.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>설명

`const_iterator`는 제어되는 시퀀스의 상수 정방향 반복기로 사용될 수 있는 개체를 설명합니다. 여기서는 구현에서 정의된 형식의 동의어로 설명됩니다.

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

전방 목록의 요소에 대 한 포인터를 제공 하는 형식입니다 **`const`** .

```cpp
typedef typename Allocator::const_pointer
    const_pointer;
```

### <a name="remarks"></a>설명

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

정방향 목록의 요소에 대한 상수 참조를 제공하는 형식입니다.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>설명

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

반복기가 가리키는 요소 사이의 범위에 있는 정방향 목록의 요소 수를 나타내는 데 사용할 수 있는 부호 있는 정수 형식입니다.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>설명

`difference_type`은 제어되는 시퀀스에서 두 요소의 주소 간 차이점을 나타낼 수 있는 개체를 설명합니다.

## <a name="emplace_after"></a><a name="emplace_after"></a> emplace_after

이동 후 지정된 위치 뒤에 새 요소를 생성합니다.

```cpp
template <class T>
iterator emplace_after(const_iterator Where, Type&& val);
```

### <a name="parameters"></a>매개 변수

*위치*\
대상 정방향 목록에서 새 요소가 생성된 위치입니다.

*짧은*\
생성자 인수입니다.

### <a name="return-value"></a>반환 값

새로 삽입된 요소를 지정하는 반복기입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 제어 *되* 는 시퀀스에서가 가리키는 요소 바로 뒤에 생성자 인수 *val* 을 사용 하 여 요소를 삽입 합니다. 그렇지 않으면 해당 동작은 [forward_list::insert_after](#insert_after)와 동일합니다.

## <a name="emplace_front"></a><a name="emplace_front"></a> emplace_front

생성된 요소를 목록 시작 부분에 추가합니다.

```cpp
template <class Type>
    void emplace_front(Type&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
정방향 목록의 시작에 추가된 요소입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 제어되는 시퀀스의 끝에 생성자 인수 `_ val`이 있는 요소를 삽입합니다.

예외가 throw되면 컨테이너는 변경되지 않은 상태로 유지되며 예외가 다시 throw됩니다.

## <a name="empty"></a><a name="empty"></a> 비우려면

정방향 목록이 비어 있는지 테스트합니다.

```cpp
bool empty() const;
```

### <a name="return-value"></a>반환 값

**`true`** 전방 목록이 비어 있으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="end"></a><a name="end"></a> end

정방향 목록에서 마지막 요소 다음에 나오는 위치의 주소를 지정하는 반복기를 반환합니다.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>반환 값

시퀀스의 끝 바로 다음을 가리키는 정방향 반복기입니다.

## <a name="erase_after"></a><a name="erase_after"></a> erase_after

정방향 목록의 지정된 위치 뒤에서 요소를 제거합니다.

```cpp
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```

### <a name="parameters"></a>매개 변수

*위치*\
대상 정방향 목록에서 요소가 지워진 위치입니다.

*기본*\
지울 범위의 시작입니다.

*최신*\
지울 범위의 끝입니다.

### <a name="return-value"></a>반환 값

제거되는 요소 뒤에 남아 있는 첫 번째 요소를 지정하는 반복기이거나, 남아 있는 요소가 없는 경우에는 [forward_list::end](#end)입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 제어 되는 시퀀스의 요소를 *Where* 바로 뒤에서 제거 합니다.

두 번째 멤버 함수는 `( first,  last)` 범위(끝점은 포함되지 않음)에 있는 제어되는 시퀀스의 요소를 제거합니다.

`N` 요소를 지우면 `N` 소멸자가 호출됩니다. [다시 할당](../standard-library/forward-list-class.md)이 수행되므로 지워진 요소에 대한 반복기와 참조가 무효화됩니다.

멤버 함수는 예외를 throw하지 않습니다.

## <a name="forward_list"></a><a name="forward_list"></a> forward_list

`forward_list` 형식의 개체를 생성합니다.

```cpp
forward_list();
explicit forward_list(const Allocator& Al);
explicit forward_list(size_type Count);
forward_list(size_type Count, const Type& Val);
forward_list(size_type Count, const Type& Val, const Allocator& Al);
forward_list(const forward_list& Right);
forward_list(const forward_list& Right, const Allocator& Al);
forward_list(forward_list&& Right);
forward_list(forward_list&& Right, const Allocator& Al);
forward_list(initializer_list<Type> IList, const Alloc& Al);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>매개 변수

*항상*\
이 개체에 사용할 할당자 클래스입니다.

*수*\
생성된 목록의 요소 수입니다.

*짧은*\
생성된 목록에 있는 요소의 값입니다.

*오른쪽*\
생성된 목록이 복사본으로 지정될 목록입니다.

*기본*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*최신*\
복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.

*IList*\
복사할 initializer_list입니다.

### <a name="remarks"></a>설명

모든 생성자는 [할당자](../standard-library/allocator-class.md)를 저장하고 제어되는 시퀀스를 초기화합니다. 할당자 개체는 *Al* 인수입니다 (있는 경우). 복사 생성자의 경우 `right.get_allocator()`입니다. 그렇지 않으면 `Allocator()`입니다.

처음 두 생성자는 빈 초기 제어되는 시퀀스를 지정합니다.

세 번째 생성자는 값의 *Count* 요소 반복을 지정 합니다 `Type()` .

네 번째 및 다섯 번째 생성자는 값 *Val* 의 *Count* 요소 반복을 지정 합니다.

여섯 번째 생성자는 *Right* 로 제어 되는 시퀀스의 복사본을 지정 합니다. `InputIterator`가 정수 형식이면 다음 두 생성자가 `(Type)Last` 값의 `(size_type)First` 요소 반복을 지정합니다. 그렇지 않으면 다음 두 생성자는 시퀀스 `[First, Last)`를 지정합니다.

아홉 번째 및 열 번째 생성자는 여섯 번째와 같지만 [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) 참조를 포함합니다.

마지막 생성자는 `initializer_list<Type>` 클래스의 개체를 사용하여 초기 제어되는 시퀀스를 지정합니다.

## <a name="front"></a><a name="front"></a> 앞뒤

정방향 목록의 첫 번째 요소에 대한 참조를 반환합니다.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>반환 값

비어 있지 않아야 하는 제어된 시퀀스의 첫 번째 요소에 대한 참조입니다.

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

정방향 목록을 생성하는 데 사용되는 할당자 개체의 복사본을 반환합니다.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>반환 값

저장된 [할당자](../standard-library/allocator-class.md) 개체입니다.

## <a name="insert_after"></a><a name="insert_after"></a> insert_after

정방향 목록의 지정된 위치 뒤에 요소를 추가합니다.

```cpp
iterator insert_after(const_iterator Where, const Type& Val);
void insert_after(const_iterator Where, size_type Count, const Type& Val);
void insert_after(const iterator Where, initializer_list<Type> IList);
iterator insert_after(const_iterator Where, Type&& Val);
template <class InputIterator>
    void insert_after(const_iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>매개 변수

*위치*\
대상 정방향 목록에서 첫 번째 요소가 삽입된 위치입니다.

*수*\
삽입할 요소의 수입니다.

*기본*\
삽입 범위의 시작입니다.

*최신*\
삽입 범위의 끝입니다.

*짧은*\
정방향 목록에 추가된 요소입니다.

*IList*\
삽입할 initializer_list입니다.

### <a name="return-value"></a>반환 값

새로 삽입된 요소(첫 번째 및 마지막 멤버 함수만)를 지정하는 반복기입니다.

### <a name="remarks"></a>설명

각 멤버 함수는 제어 되는 시퀀스의 Where가 가리키는 요소 바로 뒤에 삽입 됩니다. *여기* 에는 나머지 피연산자가 지정 하는 시퀀스가 있습니다.

첫 번째 멤버 함수는 값 *Val* 이 있는 요소를 삽입 하 고 새로 삽입 된 요소를 지정 하는 반복기를 반환 합니다.

두 번째 멤버 함수는 값 *Val* 의 *Count* 요소 반복을 삽입 합니다.

`InputIterator`가 정수 형식이면 세 번째 멤버 함수는 `insert(it, (size_type)First, (Type)Last)`와 동일하게 동작합니다. 그렇지 않으면 시퀀스 `[First, Last)`를 삽입합니다. 대체 시퀀스는 초기 제어되는 시퀀스와 겹치면 안 됩니다.

네 번째 멤버 함수는 `initializer_list<Type>` 클래스의 개체로 지정되는 시퀀스를 삽입합니다.

마지막 멤버 함수는 첫 번째와 같지만 [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) 참조를 포함합니다.

`N` 요소를 삽입하면 `N` 생성자가 호출됩니다. [다시 할당](../standard-library/forward-list-class.md)이 수행되지만 반복기나 참조가 무효화되지 않습니다.

하나 이상의 요소를 삽입하는 동안 예외가 throw되면 컨테이너는 변경되지 않고 예외가 다시 throw됩니다.

## <a name="iterator"></a><a name="iterator"></a> 반복

정방향 목록에 대한 반복기를 제공하는 형식입니다.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>설명

`iterator`는 제어되는 시퀀스의 정방향 반복기로 사용될 수 있는 개체를 설명합니다. 여기서는 구현에서 정의된 형식의 동의어로 설명됩니다.

## <a name="max_size"></a><a name="max_size"></a> max_size

정방향 목록의 최대 길이를 반환합니다.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>반환 값

개체가 제어할 수 있는 가장 긴 시퀀스의 길이입니다.

### <a name="remarks"></a>설명

## <a name="merge"></a><a name="merge"></a> 결합

두 개의 정렬된 시퀀스를 선형 시간의 단일 정렬된 시퀀스로 결합합니다. 인수 목록에서 요소를 제거하고 이 `forward_list`에 삽입합니다. `merge`를 호출하기 전에 같은 비교 함수 개체별로 두 목록을 정렬해야 합니다. 결합된 목록은 해당 비교 함수 개체별로 정렬됩니다.

```cpp
void merge(forward_list& right);
template <class Predicate>
    void merge(forward_list& right, Predicate comp);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
병합할 소스 정방향 목록입니다.

*생략*\
요소를 정렬하는 데 사용되는 비교 함수 개체입니다.

### <a name="remarks"></a>설명

`forward_list::merge` 에서 요소를 제거 `forward_list` `right` 하 고이에 삽입 `forward_list` 합니다. 두 시퀀스는 모두 아래 설명된 동일한 조건자별로 순서가 지정되어야 합니다. 결합된 시퀀스도 비교 함수 개체별로 순서가 지정되어야 합니다.

위치 `i` 및 `j`에서 요소를 지정하는 반복기 `Pi` 및 `Pj`의 경우 첫 번째 멤버 함수는 `i < j`가 실행될 때마다 순서 `!(*Pj < *Pi)`를 적용합니다. 요소는 순서 대로 정렬 됩니다 `ascending` . 두 번째 멤버 함수는 항상 순서를 적용 합니다 `! comp(*Pj, *Pi)` `i < j` .

원래 제어되는 시퀀스의 요소 쌍은 결과 제어되는 시퀀스에서 반전되지 않습니다. 결과 제어되는 시퀀스의 요소 쌍이 같은 것으로 확인되면(`!(*Pi < *Pj) && !(*Pj < *Pi)`) 원래 제어되는 시퀀스의 요소가 `right`에서 제어되는 시퀀스의 요소 앞에 나타납니다.

`comp`가 예외를 throw하는 경우에만 예외가 발생합니다. 이 경우 제어되는 시퀀스는 지정되지 않은 순서로 남아 있고 예외가 다시 throw됩니다.

## <a name="operator"></a><a name="op_eq"></a> 연산자 =

정방향 목록의 요소를 다른 정방향 목록의 복사본으로 바꿉니다.

```cpp
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
정방향 목록으로 복사되는 정방향 목록입니다.

*IList*\
`Type` 형식 요소의 시퀀스처럼 동작하는 중괄호로 묶인 이니셜라이저 목록입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 연산자는 제어 되는 시퀀스를 *right* 로 제어 되는 시퀀스의 복사본으로 바꿉니다.

두 번째 멤버 연산자는 `initializer_list<Type>` 클래스 개체의 제어되는 시퀀스를 대체합니다.

세 번째 멤버 연산자는 첫 번째 멤버 연산자와 동일하지만 [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) 참조를 포함합니다.

## <a name="pointer"></a><a name="pointer"></a> 포인터

정방향 목록의 요소에 대한 포인터를 제공하는 형식입니다.

```cpp
typedef typename Allocator::pointer pointer;
```

## <a name="pop_front"></a><a name="pop_front"></a> pop_front

정방향 목록의 시작 부분에 있는 요소를 삭제합니다.

```cpp
void pop_front();
```

### <a name="remarks"></a>설명

비어 있지 않아야 하는 정방향 목록의 첫 번째 요소입니다.

멤버 함수는 예외를 throw하지 않습니다.

## <a name="push_front"></a><a name="push_front"></a> push_front

정방향 목록의 시작 부분에 요소를 추가합니다.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
정방향 목록의 시작에 추가된 요소입니다.

### <a name="remarks"></a>설명

예외가 throw되면 컨테이너는 변경되지 않은 상태로 유지되며 예외가 다시 throw됩니다.

## <a name="reference"></a><a name="reference"></a> 참조일

정방향 목록의 요소에 대한 참조를 제공하는 형식입니다.

```cpp
typedef typename Allocator::reference reference;
```

## <a name="remove"></a><a name="remove"></a> 삭제

정방향 목록에서 지정된 값과 일치하는 요소를 지웁니다.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>매개 변수

*짧은*\
요소에 값이 있는 경우 목록에서 해당 요소가 제거됩니다.

### <a name="remarks"></a>설명

멤버 함수는 `*P ==  val`인 경우 반복기 `P`로 지정된 모든 요소를 제어되는 시퀀스에서 제거합니다.

멤버 함수는 예외를 throw하지 않습니다.

## <a name="remove_if"></a><a name="remove_if"></a> remove_if

지정된 조건자를 충족하는 요소를 정방향 목록에서 지웁니다.

```cpp
template <class Predicate>
    void remove_if(Predicate pred);
```

### <a name="parameters"></a>매개 변수

*pred*\
요소로 충족된 경우 목록에서 요소가 삭제되는 단항 조건자입니다.

### <a name="remarks"></a>설명

멤버 함수는 `pred(*P)`가 true인 경우 반복기 `P`로 지정된 모든 요소를 제어되는 시퀀스에서 제거합니다.

*Pred* 가 예외를 throw 하는 경우에만 예외가 발생 합니다. 이 경우 제어되는 시퀀스는 지정되지 않은 상태로 남아 있고 예외가 다시 throw됩니다.

## <a name="resize"></a><a name="resize"></a> 조정해

정방향 목록의 새 크기를 지정합니다.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```

### <a name="parameters"></a>매개 변수

*_Newsize*\
크기 조정된 정방향 목록의 요소 수입니다.

*짧은*\
안쪽 여백에 사용할 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 예측이 목록에 있는 요소 수가 *_Newsize* 되는지 확인 합니다. 제어 되는 시퀀스를 더 길게 만들어야 하는 경우 첫 번째 멤버 함수는 값 `Type()` 이 인 요소를 추가 하는 반면 두 번째 멤버 함수는 값 *val* 을 사용 하 여 요소를 추가 합니다. 제어되는 시퀀스 길이를 줄이기 위해 두 멤버 함수는 모두 실제로 `erase_after(begin() + _Newsize - 1, end())`를 호출합니다.

## <a name="reverse"></a><a name="reverse"></a> 되돌립니다

정방향 목록에 요소가 나타나는 순서를 반대로 바꿉니다.

```cpp
void reverse();
```

## <a name="size_type"></a><a name="size_type"></a> size_type

두 요소 사이의 부호가 없는 거리를 나타내는 형식입니다.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="remarks"></a>설명

부호 없는 정수 형식은 제어되는 시퀀스의 길이를 나타낼 수 있는 개체를 설명합니다.

## <a name="sort"></a><a name="sort"></a> 정렬

오름차순 또는 조건자를 통해 지정된 순서로 요소를 정렬합니다.

```cpp
void sort();
template <class Predicate>
void sort(Predicate pred);
```

### <a name="parameters"></a>매개 변수

*pred*\
순서 지정 조건자입니다.

### <a name="remarks"></a>설명

두 멤버 함수는 모두 제어되는 시퀀스에서 요소의 순서를 아래 설명된 조건자별로 지정합니다.

위치 `i` 및 `j`에서 요소를 지정하는 반복기 `Pi` 및 `Pj`의 경우 첫 번째 멤버 함수는 `i < j`가 실행될 때마다 순서 `!(*Pj < *Pi)`를 적용합니다. 요소는 순서 대로 정렬 됩니다 `ascending` . 멤버 템플릿 함수는 항상 순서를 적용 합니다 `! pred(*Pj, *Pi)` `i < j` . 원래 제어되는 시퀀스의 순서가 지정된 요소 쌍은 결과 제어되는 시퀀스에서 반전되지 않습니다. 정렬이 안정적입니다.

*Pred* 가 예외를 throw 하는 경우에만 예외가 발생 합니다. 이 경우 제어되는 시퀀스는 지정되지 않은 순서로 남아 있고 예외가 다시 throw됩니다.

## <a name="splice_after"></a><a name="splice_after"></a> splice_after

요소를 원본 forward_list에서 제거한 다음 대상 forward_list에 삽입합니다.

```cpp
// insert the entire source forward_list
void splice_after(const_iterator Where, forward_list& Source);
void splice_after(const_iterator Where, forward_list&& Source);

// insert one element of the source forward_list
void splice_after(const_iterator Where, forward_list& Source, const_iterator Iter);
void splice_after(const_iterator Where, forward_list&& Source, const_iterator Iter);

// insert a range of elements from the source forward_list
void splice_after(
    const_iterator Where,
    forward_list& Source,
    const_iterator First,
    const_iterator Last);

void splice_after(
    const_iterator Where,
    forward_list&& Source,
    const_iterator First,
    const_iterator Last);
```

### <a name="parameters"></a>매개 변수

*위치*\
대상 forward_list의 위치로, 이 위치 앞에서 삽입합니다.

*원본*\
대상 forward_list으로 삽입할 원본 forward_list입니다.

*Iter*\
원본 forward_list에서 삽입할 요소입니다.

*기본*\
원본 forward_list에서 삽입할 범위 내 첫 번째 요소입니다.

*최신*\
원본 forward_list에서 삽입할 범위를 벗어난 첫 번째 위치입니다.

### <a name="remarks"></a>설명

멤버 함수의 첫 번째 쌍은 *원본* 으로 제어 되는 시퀀스를 Where가 가리키는 제어 *되* 는 시퀀스의 요소 바로 뒤에 삽입 합니다. 또한 *소스* 에서 모든 요소를 제거 합니다. `&Source`와 같지 않아야 **`this`** 합니다.

멤버 함수의 두 번째 쌍은 *소스* 에 의해 제어 되는 시퀀스에서 *Iter* 바로 뒤에 있는 요소를 제거 하 여 제어 *되* 는 시퀀스에서가 가리키는 요소 바로 뒤에 삽입 합니다. `Where == Iter || Where == ++Iter`인 경우 아무 것도 변경되지 않습니다.

멤버 함수 (원거리 스플라이스)의 세 번째 쌍은가 `(First, Last)` 가리키는 제어 *되* 는 시퀀스의 요소 바로 뒤에 *소스로* 제어 되는 하위 범위를 삽입 합니다. 또한 *원본* 으로 제어 되는 시퀀스에서 원래 하위 범위를 제거 합니다. 인 경우 `&Source == this` 범위는 `(First, Last)` *Where* 가 가리키는 요소를 포함 하지 않아야 합니다.

범위가 지정된 스플라이스가 `N`개 요소 및 `&Source != this`를 삽입하면 [iterator](#iterator) 클래스의 개체가 `N`배 증분됩니다.

스플라이스된 요소를 지정하는 어떤 반복기, 포인터 또는 참조도 잘못되지 않습니다.

### <a name="example"></a>예제

```cpp
// forward_list_splice_after.cpp
// compile with: /EHsc /W4
#include <forward_list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    forward_list<int> c1{ 10, 11 };
    forward_list<int> c2{ 20, 21, 22 };
    forward_list<int> c3{ 30, 31 };
    forward_list<int> c4{ 40, 41, 42, 43 };

    forward_list<int>::iterator where_iter;
    forward_list<int>::iterator first_iter;
    forward_list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice_after(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice_after(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    c2.splice_after(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = (10) (11)c2 = (20) (21) (22)c3 = (30) (31)c4 = (40) (41) (42) (43)After splicing c1 into c2:c1 =c2 = (20) (21) (10) (11) (22)After splicing the first element of c3 into c2:c3 = (30)c2 = (20) (21) (31) (10) (11) (22)After splicing a range of c4 into c2:c4 = (40) (41)c2 = (20) (21) (42) (43) (31) (10) (11) (22)
```

## <a name="swap"></a><a name="swap"></a> 스왑을

두 정방향 목록의 요소를 교환합니다.

```cpp
void swap(forward_list& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 요소를 제공하는 정방향 목록입니다.

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 **`*this`** 과 *오른쪽* 으로 바꿉니다. `get_allocator() ==  right.get_allocator()`인 경우 일정한 시간에 이 작업을 수행하고, 예외를 throw하지 않고, 두 개의 제어되는 시퀀스에서 요소를 지정하는 참조, 포인터 또는 반복기를 무효화하지 않습니다. 그렇지 않으면 두 개의 제어되는 시퀀스에 있는 요소 수에 비례하여 많은 요소 할당 및 생성자 호출을 수행합니다.

## <a name="unique"></a><a name="unique"></a> 고유

동일한 요소의 모든 연속 그룹에서 첫 번째 요소를 제외하고 모두 제거합니다.

```cpp
void unique();
template <class BinaryPredicate>
void unique(BinaryPredicate comp);
```

### <a name="parameters"></a>매개 변수

*생략*\
연속 요소를 비교하는 데 사용되는 이진 조건자입니다.

### <a name="remarks"></a>설명

각 고유 요소의 첫 번째 요소를 유지하고 나머지를 제거합니다. 목록에서 동일한 값의 요소가 인접하도록 요소를 정렬해야 합니다.

첫 번째 멤버 함수는 이전 요소와 같은 것으로 확인된 모든 요소를 제어되는 시퀀스에서 제거합니다. 위치 `i` 및 `j`에서 요소를 지정하는 반복기 `Pi` 및 `Pj`의 경우 두번째 멤버 함수는 `i + 1 == j &&  comp(*Pi, *Pj)`에 해당하는 모든 요소를 제거합니다.

길이가 `N`(> 0)인 제어되는 시퀀스의 경우 조건자 `comp(*Pi, *Pj)`는 `N - 1`번 평가됩니다.

`comp`가 예외를 throw하는 경우에만 예외가 발생합니다. 이 경우 제어되는 시퀀스는 지정되지 않은 상태로 남아 있고 예외가 다시 throw됩니다.

## <a name="value_type"></a><a name="value_type"></a> value_type

정방향 목록에 저장된 요소의 형식을 나타내는 형식입니다.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Type`의 동의어입니다.
