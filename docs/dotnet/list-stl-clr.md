---
description: '자세히 알아보기: 목록 (STL/CLR)'
title: list(STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::list
- cliext::list::assign
- cliext::list::back
- cliext::list::back_item
- cliext::list::begin
- cliext::list::clear
- cliext::list::const_iterator
- cliext::list::const_reference
- cliext::list::const_reverse_iterator
- cliext::list::difference_type
- cliext::list::empty
- cliext::list::end
- cliext::list::erase
- cliext::list::front
- cliext::list::front_item
- cliext::list::generic_container
- cliext::list::generic_iterator
- cliext::list::generic_reverse_iterator
- cliext::list::generic_value
- cliext::list::insert
- cliext::list::iterator
- cliext::list::list
- cliext::list::merge
- cliext::list::operator=
- cliext::list::pop_back
- cliext::list::pop_front
- cliext::list::push_back
- cliext::list::push_front
- cliext::list::rbegin
- cliext::list::reference
- cliext::list::remove
- cliext::list::remove_if
- cliext::list::rend
- cliext::list::resize
- cliext::list::reverse
- cliext::list::reverse_iterator
- cliext::list::size
- cliext::list::size_type
- cliext::list::sort
- cliext::list::splice
- cliext::list::swap
- cliext::list::to_array
- cliext::list::unique
- cliext::list::value_type
- cliext::operator!=(list)
- cliext::operator<(list)
- cliext::operator<=(list)
- cliext::operator==(list)
- cliext::operator>(list)
- cliext::operator>=(list)
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- list member [STL/CLR]
- merge member [STL/CLR]
- operator= member [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- remove member [STL/CLR]
- remove_if member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- sort member [STL/CLR]
- splice member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- unique member [STL/CLR]
- value_type member [STL/CLR]
- operator!=(list) member [STL/CLR]
- operator<(list) member [STL/CLR]
- operator<=(list) member [STL/CLR]
- operator==(list) member [STL/CLR]
- operator>(list) member [STL/CLR]
- operator>=(list) member [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
ms.openlocfilehash: b23bc3f53cc13338e09ee8a6171d3da3b0b75d67
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344512"
---
# <a name="list-stlclr"></a>list(STL/CLR)

이 템플릿 클래스는 양방향 액세스를 포함 하는 다양 한 길이의 요소 시퀀스를 제어 하는 개체를 설명 합니다. 컨테이너를 사용 하 여 요소 `list` 시퀀스를 각각 하나의 요소를 저장 하는 노드의 양방향 연결 목록으로 관리 합니다.

아래 설명에서 후자가 `GValue` ref 형식이 아닌 경우는 *값* 과 같습니다 `Value^` .

## <a name="syntax"></a>구문

```cpp
template<typename Value>
    ref class list
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        Microsoft::VisualC::StlClr::IList<GValue>
    { ..... };
```

### <a name="parameters"></a>매개 변수

*값*<br/>
제어되는 시퀀스의 요소 형식입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<cliext/list>

**네임 스페이스:** cliext

## <a name="declarations"></a>선언

|형식 정의|설명|
|---------------------|-----------------|
|[list::const_iterator(STL/CLR)](#const_iterator)|제어되는 시퀀스에 대한 상수 반복기의 형식입니다.|
|[list::const_reference(STL/CLR)](#const_reference)|요소에 대한 상수 참조의 형식입니다.|
|[list::const_reverse_iterator(STL/CLR)](#const_reverse_iterator)|제어되는 시퀀스에 대한 상수 역방향 반복기의 형식입니다.|
|[list::difference_type(STL/CLR)](#difference_type)|두 요소 사이의 부호가 있는 거리의 형식입니다.|
|[list::generic_container(STL/CLR)](#generic_container)|컨테이너에 대 한 제네릭 인터페이스의 형식입니다.|
|[list::generic_iterator(STL/CLR)](#generic_iterator)|컨테이너의 제네릭 인터페이스에 대 한 반복기의 형식입니다.|
|[list::generic_reverse_iterator(STL/CLR)](#generic_reverse_iterator)|컨테이너의 제네릭 인터페이스에 대 한 역방향 반복기의 형식입니다.|
|[list::generic_value(STL/CLR)](#generic_value)|컨테이너의 제네릭 인터페이스에 대 한 요소의 형식입니다.|
|[list::iterator(STL/CLR)](#iterator)|제어되는 시퀀스에 대한 반복기의 형식입니다.|
|[list::reference(STL/CLR)](#reference)|요소에 대한 참조의 형식입니다.|
|[list::reverse_iterator(STL/CLR)](#reverse_iterator)|제어되는 시퀀스에 대한 반대 반복기의 형식입니다.|
|[list::size_type(STL/CLR)](#size_type)|두 요소 사이의 부호가 있는 거리의 형식입니다.|
|[list::value_type(STL/CLR)](#value_type)|요소의 형식입니다.|

|멤버 함수|설명|
|---------------------|-----------------|
|[list::assign(STL/CLR)](#assign)|모든 요소를 바꿉니다.|
|[list::back(STL/CLR)](#back)|마지막 요소에 액세스합니다.|
|[list::begin(STL/CLR)](#begin)|제어되는 시퀀스의 시작을 지정합니다.|
|[list::clear(STL/CLR)](#clear)|모든 요소를 제거합니다.|
|[list::empty(STL/CLR)](#empty)|요소가 있는지 여부를 테스트합니다.|
|[list::end(STL/CLR)](#end)|제어되는 시퀀스의 끝을 지정합니다.|
|[list::erase(STL/CLR)](#erase)|지정된 위치에 있는 요소를 제거합니다.|
|[list::front(STL/CLR)](#front)|첫 번째 요소에 액세스합니다.|
|[list::insert(STL/CLR)](#insert)|지정 된 위치에 요소를 추가 합니다.|
|[list::list(STL/CLR)](#list)|컨테이너 개체를 만듭니다.|
|[list::merge(STL/CLR)](#merge)|순서가 지정된 두 개의 제어되는 시퀀스를 병합합니다.|
|[list::pop_back(STL/CLR)](#pop_back)|마지막 요소를 제거 합니다.|
|[list::pop_front(STL/CLR)](#pop_front)|첫 번째 요소를 제거 합니다.|
|[list::push_back(STL/CLR)](#push_back)|새 마지막 요소를 추가 합니다.|
|[list::push_front(STL/CLR)](#push_front)|새 첫 번째 요소를 추가 합니다.|
|[list::rbegin(STL/CLR)](#rbegin)|제어되는 역방향 시퀀스의 시작을 지정합니다.|
|[list::remove(STL/CLR)](#remove)|지정 된 값을 가진 요소를 제거 합니다.|
|[list::remove_if(STL/CLR)](#remove_if)|지정 된 테스트를 통과 하는 요소를 제거 합니다.|
|[list::rend(STL/CLR)](#rend)|제어되는 역방향 시퀀스의 끝을 지정합니다.|
|[list::resize(STL/CLR)](#resize)|요소 수를 변경합니다.|
|[list::reverse(STL/CLR)](#reverse)|제어 되는 시퀀스를 반대로 바꿉니다.|
|[list::size(STL/CLR)](#size)|요소 수를 계산합니다.|
|[list::sort(STL/CLR)](#sort)|제어되는 시퀀스를 정렬합니다.|
|[list::splice(STL/CLR)](#splice)|노드 간의 연결을 다시 붙입니다.|
|[list::swap(STL/CLR)](#swap)|두 컨테이너의 내용을 바꿉니다.|
|[list::to_array(STL/CLR)](#to_array)|제어 되는 시퀀스를 새 배열에 복사 합니다.|
|[list::unique(STL/CLR)](#unique)|지정된 테스트를 통과하는 인접 요소를 제거합니다.|

|속성|설명|
|--------------|-----------------|
|[list::back_item(STL/CLR)](#back_item)|마지막 요소에 액세스합니다.|
|[list::front_item(STL/CLR)](#front_item)|첫 번째 요소에 액세스합니다.|

|연산자|설명|
|--------------|-----------------|
|[list::operator=(STL/CLR)](#op_as)|제어되는 시퀀스를 바꿉니다.|
|[operator! = (목록) (STL/CLR)](#op_neq)|`list`개체가 다른 개체와 다른 지 여부를 확인 `list` 합니다.|
|[연산자< (목록) (STL/CLR)](#op_lt)|`list`개체가 다른 개체 보다 작거나 같은지 여부를 확인 `list` 합니다.|
|[연산자<= (목록) (STL/CLR)](#op_lteq)|`list`개체가 다른 개체 보다 작거나 같은지 여부를 확인 `list` 합니다.|
|[operator = = (목록) (STL/CLR)](#op_eq)|`list`개체가 다른 개체와 같은지 여부를 확인 `list` 합니다.|
|[연산자> (목록) (STL/CLR)](#op_gt)|`list`개체가 다른 개체 보다 큰지 여부를 확인 `list` 합니다.|
|[operator>= (list)(STL/CLR)](#op_gteq)|`list`개체가 다른 개체 보다 크거나 같은지 여부를 확인 `list` 합니다.|

## <a name="interfaces"></a>인터페이스

|인터페이스|설명|
|---------------|-----------------|
|<xref:System.ICloneable>|개체를 복제 합니다.|
|<xref:System.Collections.IEnumerable>|요소를 순서 대로 이동 합니다.|
|<xref:System.Collections.ICollection>|요소 그룹을 유지 관리 합니다.|
|<xref:System.Collections.Generic.IEnumerable%601>|형식화 된 요소를 통해 시퀀싱 합니다.|
|<xref:System.Collections.Generic.ICollection%601>|형식화 된 요소의 그룹을 유지 관리 합니다.|
|IList\<Value>|일반 컨테이너를 유지 관리 합니다.|

## <a name="remarks"></a>설명

개체는 양방향 링크 목록에서 개별 노드로 제어 되는 시퀀스에 대 한 저장소를 할당 하 고 해제 합니다. 노드 간에 링크를 변경 하 여 요소를 다시 정렬 합니다. 즉, 노드 내용을 다른 노드로 복사 하지 않습니다. 즉, 나머지 요소를 방해 하지 않고 요소를 자유롭게 삽입 하 고 제거할 수 있습니다. 따라서 목록은 템플릿 클래스 [큐 (stl/clr)](../dotnet/queue-stl-clr.md) 또는 템플릿 클래스 [스택 (stl/clr)](../dotnet/stack-stl-clr.md)의 기본 컨테이너에 적합 한 후보입니다.

`list`개체는 양방향 반복기를 지원 합니다. 즉, 제어 되는 시퀀스에서 요소를 지정 하는 반복기를 사용 하 여 인접 한 요소를 한 단계씩 실행 할 수 있습니다. 특수 헤드 노드는 [list:: end (STL/CLR)](#end)에서 반환 된 반복기에 해당 `()` 합니다. 제어 되는 시퀀스의 마지막 요소 (있는 경우)에 도달할 때까지이 반복기를 줄일 수 있습니다. 목록 반복기를 증가 시켜 헤드 노드에 도달할 수 있습니다. 그런 다음와 비교 `end()` 합니다. 그러나에서 반환 된 반복기는 역 참조할 수 없습니다 `end()` .

숫자 위치가 지정 된 경우에는 임의 액세스 반복기를 필요로 하는 목록 요소를 직접 참조할 수 없습니다. 따라서 목록은 템플릿 클래스 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)의 기본 컨테이너로 사용할 *수 없습니다* .

목록 반복기는 연결 된 목록 노드에 대 한 핸들을 저장 합니다. 그러면 핸들은 연결 된 컨테이너에 저장 됩니다. 반복기는 연결 된 컨테이너 개체에만 사용할 수 있습니다. 목록 반복기는 연결 된 목록 노드가 일부 목록과 연결 되어 있으면 유효한 상태로 유지 됩니다. 또한 유효한 반복기는 dereferencable입니다 .이 반복기를 사용 하 여 지정 된 요소 값을 액세스 하거나 변경할 수 있습니다 .이는와 같지 않은 경우 `end()` 입니다.

요소를 지우거 나 제거 하면 저장 된 값에 대 한 소멸자가 호출 됩니다. 컨테이너를 삭제 하면 모든 요소가 지워집니다. 따라서 요소 형식이 ref 클래스 인 컨테이너는 컨테이너의 활성 요소가 없도록 합니다. 그러나 핸들의 컨테이너는 해당 요소 *를 소멸 시 키 지 않습니다.*

## <a name="members"></a>멤버

## <a name="listassign-stlclr"></a><a name="assign"></a> list:: assign (STL/CLR)

모든 요소를 바꿉니다.

### <a name="syntax"></a>구문

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>매개 변수

*count*<br/>
삽입할 요소의 수입니다.

*first*<br/>
삽입할 범위의 시작입니다.

*last*<br/>
삽입할 범위의 끝입니다.

*오른쪽*<br/>
삽입할 열거형입니다.

*짧은*<br/>
삽입할 요소의 값입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 제어 되는 시퀀스를 값 *val* 의 *count* 요소 반복으로 바꿉니다. 이를 사용 하 여 동일한 값을 갖는 요소로 컨테이너를 채웁니다.

`InIt`가 정수 형식이 면 두 번째 멤버 함수는와 동일 하 게 동작 합니다 `assign((size_type)first, (value_type)last)` . 그렇지 않으면 제어 되는 시퀀스를 [ `first` ,) 시퀀스로 바꿉니다 `last` . 이를 사용 하 여 제어 되는 시퀀스를 다른 시퀀스로 복사 합니다.

세 번째 멤버 함수는 제어 되는 시퀀스를 열거자 *오른쪽* 으로 지정 된 시퀀스로 바꿉니다. 이를 사용 하 여 제어 되는 시퀀스를 열거자에서 설명 하는 시퀀스의 복사본으로 만듭니다.

### <a name="example"></a>예제

```cpp
// cliext_list_assign.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // assign a repetition of values
    cliext::list<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an iterator range
    cliext::list<wchar_t>::iterator it = c1.end();
    c2.assign(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an enumeration
    c2.assign(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
x x x x x x
a b
a b c
```

## <a name="listback-stlclr"></a><a name="back"></a> list:: back (STL/CLR)

마지막 요소에 액세스합니다.

### <a name="syntax"></a>구문

```cpp
reference back();
```

### <a name="remarks"></a>설명

멤버 함수는 비어 있지 않아야 하는 제어 되는 시퀀스의 마지막 요소에 대 한 참조를 반환 합니다. 이를 사용 하 여 마지막 요소 (있는 경우)에 액세스 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

    // alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back() = c
a b x
```

## <a name="listback_item-stlclr"></a><a name="back_item"></a> list:: back_item (STL/CLR)

마지막 요소에 액세스합니다.

### <a name="syntax"></a>구문

```cpp
property value_type back_item;
```

### <a name="remarks"></a>설명

속성은 비어 있지 않아야 하는 제어 되는 시퀀스의 마지막 요소에 액세스 합니다. 이를 사용 하 여 마지막 요소 (있는 경우)를 읽거나 씁니다.

### <a name="example"></a>예제

```cpp
// cliext_list_back_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

    // alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back_item = c
a b x
```

## <a name="listbegin-stlclr"></a><a name="begin"></a> list:: begin (STL/CLR)

제어되는 시퀀스의 시작을 지정합니다.

### <a name="syntax"></a>구문

```cpp
iterator begin();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 첫 번째 요소 또는 빈 시퀀스의 끝 바로 다음을 지정 하는 임의 액세스 반복기를 반환 합니다. 이를 통해 제어되는 시퀀스의 `current` 시작을 지정하는 반복기를 가져올 수 있지만 제어되는 시퀀스의 길이가 변경되면 상태가 변경될 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_list_begin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);

    // alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
x y c
```

## <a name="listclear-stlclr"></a><a name="clear"></a> list:: clear (STL/CLR)

모든 요소를 제거합니다.

### <a name="syntax"></a>구문

```cpp
void clear();
```

### <a name="remarks"></a>설명

멤버 함수는 [list:: erase (stl/clr)](#erase) `(` [list:: begin (stl/clr)](#begin) `(),` [list:: end (stl/clr)](#end)를 효과적으로 호출 합니다 `())` . 이를 사용 하 여 제어 되는 시퀀스가 비어 있는지 확인 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_clear.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 0
a b
size() = 0
```

## <a name="listconst_iterator-stlclr"></a><a name="const_iterator"></a> list:: const_iterator (STL/CLR)

제어되는 시퀀스에 대한 상수 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>설명

`T2`이 형식은 제어 되는 시퀀스에 대 한 상수 임의 액세스 반복기로 사용 될 수 있는 지정 되지 않은 형식의 개체를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_const_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="listconst_reference-stlclr"></a><a name="const_reference"></a> list:: const_reference (STL/CLR)

요소에 대한 상수 참조의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>설명

요소에 대 한 상수 참조를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_list_const_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::list<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="listconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a> list:: const_reverse_iterator (STL/CLR)

제어 되는 시퀀스에 대 한 상수 역방향 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>설명

`T4`이 형식은 제어 되는 시퀀스에 대 한 상수 역방향 반복기로 사용 될 수 있는 지정 되지 않은 형식의 개체를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::list<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="listdifference_type-stlclr"></a><a name="difference_type"></a> 목록::d ifference_type (STL/CLR)

두 요소 사이의 부호가 있는 거리의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>설명

형식은 서명 된 요소 수를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_difference_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::difference_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.end();
        it != c1.begin(); --it) --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="listempty-stlclr"></a><a name="empty"></a> list:: empty (STL/CLR)

요소가 있는지 여부를 테스트합니다.

### <a name="syntax"></a>구문

```cpp
bool empty();
```

### <a name="remarks"></a>설명

멤버 함수는 빈 제어되는 시퀀스에 대해 true를 반환합니다. [List:: size (STL/CLR)](#size)와 동일 `() == 0` 합니다. 목록이 비어 있는지 여부를 테스트 하는 데 사용 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_empty.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="listend-stlclr"></a><a name="end"></a> list:: end (STL/CLR)

제어되는 시퀀스의 끝을 지정합니다.

### <a name="syntax"></a>구문

```cpp
iterator end();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 끝 바로 다음을 가리키는 임의 액세스 반복기를 반환 합니다. 이를 사용 하 여 제어 되는 시퀀스의 끝을 지정 하는 반복기를 가져옵니다. 제어 되는 시퀀스의 길이가 변경 되 면 해당 상태는 변경 되지 않습니다.

### <a name="example"></a>예제

```cpp
// cliext_list_end.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    cliext::list<wchar_t>::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);

    // alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
a x y
```

## <a name="listerase-stlclr"></a><a name="erase"></a> list:: erase (STL/CLR)

지정된 위치에 있는 요소를 제거합니다.

### <a name="syntax"></a>구문

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>매개 변수

*first*<br/>
지울 범위의 시작입니다.

*last*<br/>
지울 범위의 끝입니다.

*where*<br/>
지울 요소입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 where가 가리키는 제어 *되* 는 시퀀스의 요소를 제거 합니다. 단일 요소를 제거 하는 데 사용 합니다.

두 번째 멤버 함수는 [`first`, `last`]의 범위에서 제어되는 시퀀스의 요소를 제거합니다. 연속 된 요소를 0 개 이상 제거 하는 데 사용 합니다.

두 멤버 함수는 제거 된 요소 뒤에 남은 첫 번째 요소를 지정 하는 반복기를 반환 하거나, 이러한 요소가 없는 경우 [list:: end (STL/CLR)](#end) 를 반환 `()` 합니다.

요소를 지울 때 요소 복사본의 수는 삭제의 끝과 시퀀스의 가까운 끝 사이에 있는 요소 수의 선형입니다. 시퀀스의 한쪽 끝에서 하나 이상의 요소를 지우면 요소 복사는 발생 하지 않습니다.

### <a name="example"></a>예제

```cpp
// cliext_list_erase.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.push_back(L'd');
    c1.push_back(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    cliext::list<wchar_t>::iterator it = c1.end();
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",
        *c1.erase(c1.begin(), --it));
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
erase(begin()) = b
b c d e
erase(begin(), end()-1) = e
size() = 1
```

## <a name="listfront-stlclr"></a><a name="front"></a> list:: front (STL/CLR)

첫 번째 요소에 액세스합니다.

### <a name="syntax"></a>구문

```cpp
reference front();
```

### <a name="remarks"></a>설명

멤버 함수는 비어 있지 않아야 하는 제어 되는 시퀀스의 첫 번째 요소에 대 한 참조를 반환 합니다. 이를 사용 하 여 첫 번째 요소가 있으면이를 읽거나 씁니다.

### <a name="example"></a>예제

```cpp
// cliext_list_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

    // alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front() = a
x b c
```

## <a name="listfront_item-stlclr"></a><a name="front_item"></a> list:: front_item (STL/CLR)

첫 번째 요소에 액세스합니다.

### <a name="syntax"></a>구문

```cpp
property value_type front_item;
```

### <a name="remarks"></a>설명

속성은 비어 있지 않아야 하는 제어 되는 시퀀스의 첫 번째 요소에 액세스 합니다. 이를 사용 하 여 첫 번째 요소가 있으면이를 읽거나 씁니다.

### <a name="example"></a>예제

```cpp
// cliext_list_front_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

    // alter first item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front_item = a
x b c
```

## <a name="listgeneric_container-stlclr"></a><a name="generic_container"></a> list:: generic_container (STL/CLR)

컨테이너에 대 한 제네릭 인터페이스의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Microsoft::VisualC::StlClr::
    IList<generic_value>
    generic_container;
```

### <a name="remarks"></a>설명

이 템플릿 컨테이너 클래스에 대 한 제네릭 인터페이스를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_list_generic_container.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(gc1->end(), L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push_back(L'e');

    System::Collections::IEnumerator^ enum1 =
        gc1->GetEnumerator();
    while (enum1->MoveNext())
        System::Console::Write("{0} ", enum1->Current);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c d
a b c d e
```

## <a name="listgeneric_iterator-stlclr"></a><a name="generic_iterator"></a> list:: generic_iterator (STL/CLR)

컨테이너의 제네릭 인터페이스와 함께 사용할 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>설명

형식은이 템플릿 컨테이너 클래스의 제네릭 인터페이스와 함께 사용할 수 있는 제네릭 반복기를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_generic_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="listgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a> list:: generic_reverse_iterator (STL/CLR)

컨테이너의 제네릭 인터페이스와 함께 사용할 역방향 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseBidirectionalIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>설명

형식은이 템플릿 컨테이너 클래스의 제네릭 인터페이스와 함께 사용할 수 있는 제네릭 역방향 반복기를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c c
```

## <a name="listgeneric_value-stlclr"></a><a name="generic_value"></a> list:: generic_value (STL/CLR)

컨테이너의 제네릭 인터페이스와 함께 사용할 요소의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>설명

`GValue`이 템플릿 컨테이너 클래스의 제네릭 인터페이스에 사용할 저장 된 요소 값을 설명 하는 형식의 개체를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_list_generic_value.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="listinsert-stlclr"></a><a name="insert"></a> list:: insert (STL/CLR)

지정 된 위치에 요소를 추가 합니다.

### <a name="syntax"></a>구문

```cpp
iterator insert(iterator where, value_type val);
void insert(iterator where, size_type count, value_type val);
template<typename InIt>
    void insert(iterator where, InIt first, InIt last);
void insert(iterator where,
    System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>매개 변수

*count*<br/>
삽입할 요소의 수입니다.

*first*<br/>
삽입할 범위의 시작입니다.

*last*<br/>
삽입할 범위의 끝입니다.

*오른쪽*<br/>
삽입할 열거형입니다.

*짧은*<br/>
삽입할 요소의 값입니다.

*where*<br/>
컨테이너에서 앞에 삽입할 위치입니다.

### <a name="remarks"></a>설명

각 멤버 함수는 제어 되는 시퀀스의 *where* 가 가리키는 요소 앞에 나머지 피연산자로 지정 된 시퀀스를 삽입 합니다.

첫 번째 멤버 함수는 값 *val* 을 사용 하 여 요소를 삽입 하 고 새로 삽입 된 요소를 지정 하는 반복기를 반환 합니다. 이를 사용 하 여 반복기에서 지정 된 장소 앞에 단일 요소를 삽입 합니다.

두 번째 멤버 함수는 값 *val* 의 *count* 요소 반복을 삽입 합니다. 동일한 값의 모든 복사본 인 연속 요소를 0 개 이상 삽입 하는 데 사용 합니다.

`InIt`가 정수 형식이면 세 번째 멤버 함수는 `insert(where, (size_type)first, (value_type)last)`와 동일하게 동작합니다. 그렇지 않으면 [,) 시퀀스를 `first` 삽입 `last` 합니다. 이를 사용 하 여 다른 시퀀스에서 복사 된 0 개 이상의 연속 요소를 삽입 합니다.

네 번째 멤버 함수는 *오른쪽* 에 지정 된 시퀀스를 삽입 합니다. 이를 사용 하 여 열거자에서 설명 하는 시퀀스를 삽입 합니다.

단일 요소를 삽입할 때 요소 복사본의 수는 삽입 지점과 시퀀스의 가까운 끝 사이에 있는 요소 수의 선형입니다. 시퀀스의 한쪽 끝에 하나 이상의 요소를 삽입 하는 경우 요소 복사는 발생 하지 않습니다. `InIt` 가 입력 반복기 인 경우 세 번째 멤버 함수는 시퀀스의 각 요소에 대 한 단일 삽입을 효과적으로 수행 합니다. 그렇지 않은 경우 `N` 요소를 삽입할 때 요소 복사본의 수는 선형이 `N` 고 삽입 지점과 시퀀스의 끝 부분 사이에 있는 요소 수를 더한 값입니다.

### <a name="example"></a>예제

```cpp
// cliext_list_insert.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using iterator
    cliext::list<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a repetition of values
    cliext::list<wchar_t> c2;
    c2.insert(c2.begin(), 2, L'y');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    it = c1.end();
    c2.insert(c2.end(), c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    c2.insert(c2.begin(),   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using index
    it = c2.begin();
    ++it, ++it, ++it;
    c2.insert(it, L'z');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
a b c
insert(begin()+1, L'x') = x
a x b c
y y
y y a x b
a x b c y y a x b
```

## <a name="listiterator-stlclr"></a><a name="iterator"></a> list:: iterator (STL/CLR)

제어되는 시퀀스에 대한 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>설명

`T1`이 형식은 제어 되는 시퀀스의 임의 액세스 반복기로 사용 될 수 있는 지정 되지 않은 형식의 개체를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();

    // alter first element and redisplay
    it = c1.begin();
    *it = L'x';
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x b c
```

## <a name="listlist-stlclr"></a><a name="list"></a> list:: list (STL/CLR)

컨테이너 개체를 만듭니다.

### <a name="syntax"></a>구문

```cpp
list();
list(list<Value>% right);
list(list<Value>^ right);
explicit list(size_type count);
list(size_type count, value_type val);
template<typename InIt>
    list(InIt first, InIt last);
list(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>매개 변수

*count*<br/>
삽입할 요소의 수입니다.

*first*<br/>
삽입할 범위의 시작입니다.

*last*<br/>
삽입할 범위의 끝입니다.

*오른쪽*<br/>
삽입할 개체 또는 범위입니다.

*짧은*<br/>
삽입할 요소의 값입니다.

### <a name="remarks"></a>설명

생성자는 다음과 같습니다.

`list();`

요소가 없는 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 빈 초기 제어 되는 시퀀스를 지정 합니다.

생성자는 다음과 같습니다.

`list(list<Value>% right);`

시퀀스 [,)를 사용 하 여 제어 되는 시퀀스를 초기화 `right.begin()` `right.end()` 합니다. 이를 사용 하 여 목록 개체 *오른쪽* 에 의해 제어 되는 시퀀스의 복사본 인 초기 제어 되는 시퀀스를 지정 합니다.

생성자는 다음과 같습니다.

`list(list<Value>^ right);`

시퀀스 [,)를 사용 하 여 제어 되는 시퀀스를 초기화 `right->begin()` `right->end()` 합니다. 이를 사용 하 여 핸들이 *right* 인 목록 개체에 의해 제어 되는 시퀀스의 복사본 인 초기 제어 되는 시퀀스를 지정 합니다.

생성자는 다음과 같습니다.

`explicit list(size_type count);`

각각 값을 포함 하는 *count* 요소를 사용 하 여 제어 되는 시퀀스를 초기화 합니다 `value_type()` . 이를 사용 하 여 모든 기본 값을 갖는 요소로 컨테이너를 채웁니다.

생성자는 다음과 같습니다.

`list(size_type count, value_type val);`

각 값이 *val* 인 *count* 요소를 사용 하 여 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 동일한 값을 갖는 요소로 컨테이너를 채웁니다.

생성자는 다음과 같습니다.

`template<typename InIt>`

`list(InIt first, InIt last);`

시퀀스 [,)를 사용 하 여 제어 되는 시퀀스를 초기화 `first` `last` 합니다. 이를 사용 하 여 제어 되는 시퀀스를 다른 시퀀스의 복사본으로 만듭니다.

생성자는 다음과 같습니다.

`list(System::Collections::Generic::IEnumerable<Value>^ right);`

열거자 *권한* 으로 지정 된 시퀀스를 사용 하 여 제어 되는 시퀀스를 초기화 합니다. 이를 사용 하 여 제어 되는 시퀀스를 열거자에서 설명한 다른 시퀀스의 복사본으로 만듭니다.

### <a name="example"></a>예제

```cpp
// cliext_list_construct.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container
    cliext::list<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    // construct with a repetition of default values
    cliext::list<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // construct with a repetition of values
    cliext::list<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    cliext::list<wchar_t>::iterator it = c3.end();
    cliext::list<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    cliext::list<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    cliext::list<wchar_t> c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
0 0 0
x x x x x x
x x x x x
x x x x x x
x x x x x x
x x x x x x
```

## <a name="listmerge-stlclr"></a><a name="merge"></a> list:: merge (STL/CLR)

순서가 지정된 두 개의 제어되는 시퀀스를 병합합니다.

### <a name="syntax"></a>구문

```cpp
void merge(list<Value>% right);
template<typename Pred2>
    void merge(list<Value>% right, Pred2 pred);
```

#### <a name="parameters"></a>매개 변수

*pred*<br/>
요소 쌍에 대 한 비교자입니다.

*오른쪽*<br/>
병합할 컨테이너입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 *오른쪽* 에 의해 제어 되는 시퀀스에서 모든 요소를 제거 하 고 제어 되는 시퀀스에 삽입 합니다. 두 시퀀스를 모두 이전에 정렬 해야 하는 `operator<` 경우--두 시퀀스 중 하나를 진행 하는 동안 요소는 값을 줄여야 합니다. 또한 결과 시퀀스는를 기준으로 정렬 됩니다 `operator<` . 값이 증가 하는 두 시퀀스를 값이 증가 하는 시퀀스로 병합 하려면이 멤버 함수를 사용 합니다.

두 번째 멤버 함수는 `pred`  --  `pred(X, Y)` 시퀀스의 요소 다음에 오는 모든 요소에 대해에서 `X` 시퀀스를 정렬 하는 것을 제외 하 고 첫 번째 멤버 함수와 동일 하 게 동작 합니다 `Y` . 이를 사용 하 여 지정 하는 조건자 함수 또는 대리자를 기준으로 정렬 된 두 시퀀스를 병합 합니다.

두 함수 모두 안정적인 병합을 수행 합니다. 원래 제어 되는 시퀀스 중 하나에 있는 요소 쌍이 결과 제어 되는 시퀀스에서 반전 되지 않습니다. 또한 요소 쌍 `X` 과 `Y` 결과 제어 되는 시퀀스의 순서가 동일한 경우에는 `!(X < Y) && !(X < Y)` 원래 제어 되는 시퀀스의 요소가 *right* 로 제어 되는 시퀀스의 요소 앞에 나타납니다.

### <a name="example"></a>예제

```cpp
// cliext_list_merge.cpp
// compile with: /clr
#include <cliext/list>

typedef cliext::list<wchar_t> Mylist;
int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'c');
    c1.push_back(L'e');

    // display initial contents " a c e"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    cliext::list<wchar_t> c2;
    c2.push_back(L'b');
    c2.push_back(L'd');
    c2.push_back(L'f');

    // display initial contents " b d f"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // merge and display
    cliext::list<wchar_t> c3(c1);
    c3.merge(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());

    // sort descending, merge descending, and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.merge(c1, cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    return (0);
    }
```

```Output
a c e
b d f
a b c d e f
c2.size() = 0
e c a
f e d c b a
f e e d c c b a a
c1.size() = 0
```

## <a name="listoperator-stlclr"></a><a name="op_as"></a> list:: operator = (STL/CLR)

제어되는 시퀀스를 바꿉니다.

### <a name="syntax"></a>구문

```
list<Value>% operator=(list<Value>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
복사할 컨테이너입니다.

### <a name="remarks"></a>설명

멤버 연산자는 개체에 대해 *를 복사 하 고를 반환* **`*this`** 합니다. 이를 사용 하 여 제어 되는 시퀀스를 *오른쪽* 에 있는 제어 되는 시퀀스의 복사본으로 바꿉니다.

### <a name="example"></a>예제

```cpp
// cliext_list_operator_as.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="listpop_back-stlclr"></a><a name="pop_back"></a> 목록::p op_back (STL/CLR)

마지막 요소를 제거 합니다.

### <a name="syntax"></a>구문

```cpp
void pop_back();
```

### <a name="remarks"></a>설명

멤버 함수는 비어 있지 않아야 하는 제어 되는 시퀀스의 마지막 요소를 제거 합니다. 이를 사용 하 여 다시 목록에 한 요소를 줄입니다.

### <a name="example"></a>예제

```cpp
// cliext_list_pop_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_back();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b
```

## <a name="listpop_front-stlclr"></a><a name="pop_front"></a> 목록::p op_front (STL/CLR)

첫 번째 요소를 제거 합니다.

### <a name="syntax"></a>구문

```cpp
void pop_front();
```

### <a name="remarks"></a>설명

멤버 함수는 비어 있지 않아야 하는 제어 되는 시퀀스의 첫 번째 요소를 제거 합니다. 이를 사용 하 여 맨 앞에 있는 요소 하나 만큼 목록을 단축할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_list_pop_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_front();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
b c
```

## <a name="listpush_back-stlclr"></a><a name="push_back"></a> 목록::p ush_back (STL/CLR)

새 마지막 요소를 추가 합니다.

### <a name="syntax"></a>구문

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 `val` 시퀀스의 끝에 값이 포함 된 요소를 삽입 합니다. 이를 사용 하 여 다른 요소를 목록에 추가 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_push_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="listpush_front-stlclr"></a><a name="push_front"></a> 목록::p ush_front (STL/CLR)

새 첫 번째 요소를 추가 합니다.

### <a name="syntax"></a>구문

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 `val` 시퀀스의 시작 부분에 값이 포함 된 요소를 삽입 합니다. 이를 사용 하 여 다른 요소를 목록에 추가 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_push_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_front(L'a');
    c1.push_front(L'b');
    c1.push_front(L'c');

    // display contents " c b a"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="listrbegin-stlclr"></a><a name="rbegin"></a> list:: rbegin (STL/CLR)

제어되는 역방향 시퀀스의 시작을 지정합니다.

### <a name="syntax"></a>구문

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 마지막 요소 또는 빈 시퀀스의 시작 부분 바로 뒤를 지정 하는 역방향 반복기를 반환 합니다. 따라서 역방향 시퀀스의 `beginning`을 지정합니다. 이를 통해 역순으로 표시된 제어되는 시퀀스의 `current` 시작을 지정하는 반복기를 가져올 수 있지만 제어되는 시퀀스의 길이가 변경되면 상태가 변경될 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_list_rbegin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);

    // alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
a y x
```

## <a name="listreference-stlclr"></a><a name="reference"></a> list:: reference (STL/CLR)

요소에 대한 참조의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>설명

요소에 대 한 참조를 설명 하는 형식입니다.

### <a name="example"></a>예제

```cpp
// cliext_list_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

    // modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;

        ref += (wchar_t)(L'A' - L'a');
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
A B C
```

## <a name="listremove-stlclr"></a><a name="remove"></a> list:: remove (STL/CLR)

지정 된 값을 가진 요소를 제거 합니다.

### <a name="syntax"></a>구문

```cpp
void remove(value_type val);
```

#### <a name="parameters"></a>매개 변수

*짧은*<br/>
제거할 요소의 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 `((System::Object^)val)->Equals((System::Object^)x)` 가 true (있는 경우) 인 제어 되는 시퀀스에서 요소를 제거 합니다. 이를 사용 하 여 지정 된 값을 가진 임의의 요소를 지울 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_list_remove.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove(L'A');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove(L'b');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c
```

## <a name="listremove_if-stlclr"></a><a name="remove_if"></a> list:: remove_if (STL/CLR)

지정 된 테스트를 통과 하는 요소를 제거 합니다.

### <a name="syntax"></a>구문

```cpp
template<typename Pred1>
    void remove_if(Pred1 pred);
```

#### <a name="parameters"></a>매개 변수

*pred*<br/>
제거할 요소를 테스트 합니다.

### <a name="remarks"></a>설명

멤버 함수는가 true 인 모든 요소를 제어 되는 시퀀스에서 제거 합니다 (지우기) `X` `pred(X)` . 이를 사용 하 여 함수 또는 대리자로 지정 된 조건을 충족 하는 모든 요소를 제거 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_remove_if.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b b b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(
        cliext::equal_to<wchar_t>(), L'd'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(
        cliext::not_equal_to<wchar_t>(), L'b'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b b b c
a b b b c
b b b
```

## <a name="listrend-stlclr"></a><a name="rend"></a> list:: rend (STL/CLR)

제어되는 역방향 시퀀스의 끝을 지정합니다.

### <a name="syntax"></a>구문

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스의 시작 부분 바로 뒤를 가리키는 역방향 반복기를 반환 합니다. 따라서 역방향 시퀀스의 `end`을 지정합니다. 이를 통해 역순으로 표시된 제어되는 시퀀스의 `current` 끝을 지정하는 반복기를 가져올 수 있지만 제어되는 시퀀스의 길이가 변경되면 상태가 변경될 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_list_rend.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);

    // alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
y x c
```

## <a name="listresize-stlclr"></a><a name="resize"></a> list:: resize (STL/CLR)

요소 수를 변경합니다.

### <a name="syntax"></a>구문

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>매개 변수

*new_size*<br/>
제어 되는 시퀀스의 새 크기입니다.

*짧은*<br/>
패딩 요소의 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 [list:: size (STL/CLR)](#size) `()` 예측이가 *new_size* 를 반환 하는지 확인 합니다. 제어 되는 시퀀스를 더 길게 만들어야 하는 경우 첫 번째 멤버 함수는 값 `value_type()` 이 인 요소를 추가 하는 반면 두 번째 멤버 함수는 값 *val* 을 사용 하 여 요소를 추가 합니다. 제어 되는 시퀀스를 더 짧게 만들기 위해 두 멤버 함수는 마지막 요소 [list:: size (STL/CLR)](#size) 시간을 효과적으로 지웁니다 `() -` `new_size` . 이를 사용 하 여 제어 되는 시퀀스의 크기 *new_size* 현재 제어 되는 시퀀스를 트리밍 또는 패딩 하 여 확인 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_resize.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container and pad with default values
    cliext::list<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());
    c1.resize(4);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // resize to empty
    c1.resize(0);
    System::Console::WriteLine("size() = {0}", c1.size());

    // resize and pad
    c1.resize(5, L'x');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
0 0 0 0
size() = 0
x x x x x
```

## <a name="listreverse-stlclr"></a><a name="reverse"></a> list:: reverse (STL/CLR)

제어 되는 시퀀스를 반대로 바꿉니다.

### <a name="syntax"></a>구문

```cpp
void reverse();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스에 있는 모든 요소의 순서를 반대로 바꿉니다. 요소 목록을 반영 하는 데 사용 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_reverse.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // reverse and redisplay
    c1.reverse();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
```

## <a name="listreverse_iterator-stlclr"></a><a name="reverse_iterator"></a> list:: reverse_iterator (STL/CLR)

제어되는 시퀀스에 대한 반대 반복기의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>설명

이 형식은 제어된 시퀀스에 대해 반대 반복기로 사용될 수 있는 지정되지 않은 `T3` 형식의 개체를 설명합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();

    // alter first element and redisplay
    rit = c1.rbegin();
    *rit = L'x';
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
x b a
```

## <a name="listsize-stlclr"></a><a name="size"></a> list:: size (STL/CLR)

요소 수를 계산합니다.

### <a name="syntax"></a>구문

```cpp
size_type size();
```

### <a name="remarks"></a>설명

멤버 함수는 제어되는 시퀀스의 길이를 반환합니다. 이를 사용 하 여 현재 제어 되는 시퀀스에 있는 요소 수를 확인 합니다. 시퀀스의 크기가 0이 아니면 [목록:: empty (STL/CLR)](#empty)를 참조 하세요 `()` .

### <a name="example"></a>예제

```cpp
// cliext_list_size.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 3 starting with 3
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="listsize_type-stlclr"></a><a name="size_type"></a> list:: size_type (STL/CLR)

두 요소 사이의 부호가 있는 거리의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef int size_type;
```

### <a name="remarks"></a>설명

이 형식은 음수가 아닌 요소 수를 설명 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_size_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::size_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="listsort-stlclr"></a><a name="sort"></a> list:: sort (STL/CLR)

제어되는 시퀀스를 정렬합니다.

### <a name="syntax"></a>구문

```cpp
void sort();
template<typename Pred2>
    void sort(Pred2 pred);
```

#### <a name="parameters"></a>매개 변수

*pred*<br/>
요소 쌍에 대 한 비교자입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 제어 되는 시퀀스의 요소를 순서 대로 정렬 하 여 `operator<` 시퀀스를 진행 하면서 요소를 기준으로 정렬 하지 않습니다. 이 멤버 함수를 사용 하 여 시퀀스를 오름차순으로 정렬 합니다.

두 번째 멤버 함수는 첫 번째 멤버와 동일 하 게 동작 합니다. 단, `pred`  --  `pred(X, Y)` `X` 결과 시퀀스의 요소 다음에 오는 모든 요소에 대 한 시퀀스의 순서가 false입니다 `Y` . 이를 사용 하 여 조건자 함수 또는 대리자에 의해 지정 된 순서로 시퀀스를 정렬 합니다.

두 함수 모두 안정적 정렬을 수행 합니다. 원래 제어 되는 시퀀스의 요소 쌍은 결과 제어 되는 시퀀스에서 반전 됩니다.

### <a name="example"></a>예제

```cpp
// cliext_list_sort.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort descending and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort ascending and redisplay
    c1.sort();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
a b c
```

## <a name="listsplice-stlclr"></a><a name="splice"></a> list:: splice (STL/CLR)

노드 간 링크 다시 연결

### <a name="syntax"></a>구문

```cpp
void splice(iterator where, list<Value>% right);
void splice(iterator where, list<Value>% right,
    iterator first);
void splice(iterator where, list<Value>% right,
    iterator first, iterator last);
```

#### <a name="parameters"></a>매개 변수

*first*<br/>
Splice 범위의 시작입니다.

*last*<br/>
Splice 범위의 끝입니다.

*오른쪽*<br/>
Splice 할 컨테이너입니다.

*where*<br/>
컨테이너에서 앞으로 splice 할 위치입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 제어 되는 시퀀스에서가 가리키는 요소 *바로* 앞에에 의해 제어 *되* 는 시퀀스를 삽입 합니다. 또한 *오른쪽* 에서 모든 요소를 제거 합니다. `%right`와 같지 않아야 **`this`** 합니다. 이를 사용 하 여 한 목록을 다른 목록으로 결합 합니다.

두 번째 멤버 함수는 *오른쪽* 에 의해 제어 되는 시퀀스에서 *먼저* 가리키는 요소를 제거 하 고 *where* 가 가리키는 제어 되는 시퀀스의 요소 앞에 삽입 합니다. (인 경우 `where` `==` `first` `||` `where` `== ++first`변경 내용이 발생 하지 않습니다. 이를 사용 하 여 한 목록에 있는 단일 요소를 다른 목록으로 결합 합니다.

세 번째 멤버 함수는 [,)로 지정 된 하위 범위를 `first` `last` where가 가리키는 제어 *되* 는 시퀀스의 요소 *바로* 앞에 있는 시퀀스에서 삽입 합니다. 또한 *right* 로 제어 되는 시퀀스에서 원래 하위 범위를 제거 합니다. 인 경우 `right == this` 범위 [ `first` ,)는 `last` *where* 가 가리키는 요소를 포함 하지 않아야 합니다. 이를 사용 하 여 하위 시퀀스 0 개 이상의 요소를 한 목록에서 다른 목록으로 결합 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_splice.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // splice to a new list
    cliext::list<wchar_t> c2;
    c2.splice(c2.begin(), c1);
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return one element
    c1.splice(c1.end(), c2, c2.begin());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return remaining elements
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());
    return (0);
    }
```

```Output
a b c
c1.size() = 0
a b c
a
b c
b c a
c2.size() = 0
```

## <a name="listswap-stlclr"></a><a name="swap"></a> list:: swap (STL/CLR)

두 컨테이너의 내용을 바꿉니다.

### <a name="syntax"></a>구문

```cpp
void swap(list<Value>% right);
```

#### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
콘텐츠와 바꿀 컨테이너입니다.

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 **`*this`** 과 *오른쪽* 으로 바꿉니다. 일정 한 시간에이를 수행 하 고 예외를 throw 하지 않습니다. 이를 사용 하 여 두 컨테이너의 콘텐츠를 신속 하 게 교환할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_list_swap.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::list<wchar_t> c2(5, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x x x x x
x x x x x
a b c
```

## <a name="listto_array-stlclr"></a><a name="to_array"></a> list:: to_array (STL/CLR)

제어 되는 시퀀스를 새 배열에 복사 합니다.

### <a name="syntax"></a>구문

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>설명

멤버 함수는 제어 되는 시퀀스를 포함 하는 배열을 반환 합니다. 이를 사용 하 여 배열 형식으로 제어 되는 시퀀스의 복사본을 가져옵니다.

### <a name="example"></a>예제

```cpp
// cliext_list_to_array.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push_back(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c d
a b c
```

## <a name="listunique-stlclr"></a><a name="unique"></a> list:: unique (STL/CLR)

지정된 테스트를 통과하는 인접 요소를 제거합니다.

### <a name="syntax"></a>구문

```cpp
void unique();
template<typename Pred2>
    void unique(Pred2 pred);
```

#### <a name="parameters"></a>매개 변수

*pred*<br/>
요소 쌍에 대 한 비교자입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 이전 요소와 같은 것으로 비교 되는 모든 요소를 제어 되는 시퀀스에서 제거 합니다 `X` . 요소가 요소와 앞에 오면 `Y` `X == Y` 멤버 함수는를 제거 `Y` 합니다. 이를 사용 하 여 동일 하 게 비교 되는 인접 요소의 모든 하위 시퀀스 복사본을 하나만 제거 합니다. [List:: sort (STL/CLR)](#sort)를 호출 하는 것과 같이 제어 되는 시퀀스를 정렬 하는 경우 `()` 멤버 함수는 고유 값이 있는 요소만 남겨 둡니다. (그래서 이러한 이름을 갖습니다.)

두 번째 멤버 함수는 요소 다음에 나오는 각 요소를 제거 한다는 점을 제외 하 고 첫 번째 함수와 동일 하 게 동작 합니다 `Y` `X` `pred(X, Y)` . 이를 사용 하 여 사용자가 지정 하는 조건자 함수 또는 대리자를 만족 하는 인접 요소를 제외한 모든 하위 시퀀스의 복사본을 하나만 제거 합니다. 을 호출 하는 것과 같이 제어 되는 시퀀스를 정렬 하는 경우 `sort(pred)` 멤버 함수는 다른 요소와 동일한 순서를 갖지 않는 요소만 남겨 둡니다.

### <a name="example"></a>예제

```cpp
// cliext_list_unique.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique
    cliext::list<wchar_t> c2(c1);
    c2.unique();
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique(not_equal_to)
    c2 = c1;
    c2.unique(cliext::not_equal_to<wchar_t>());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a a b c
a b c
a a
```

## <a name="listvalue_type-stlclr"></a><a name="value_type"></a> list:: value_type (STL/CLR)

요소의 형식입니다.

### <a name="syntax"></a>구문

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>설명

형식은 템플릿 매개 변수 *값* 의 동의어입니다.

### <a name="example"></a>예제

```cpp
// cliext_list_value_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using value_type
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::list<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-list-stlclr"></a><a name="op_neq"></a> operator! = (목록) (STL/CLR)

목록이 같지 않음 비교입니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value>
    bool operator!=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 컨테이너입니다.

*오른쪽*<br/>
비교할 오른쪽 컨테이너입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `!(left == right)` . 이를 사용 하 여 두 목록을 요소 별로 비교할 때 *왼쪽* 이 *오른쪽* 과 동일 하 게 정렬 되지 않는지 여부를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_list_operator_ne.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="operatorlt-list-stlclr"></a><a name="op_lt"></a> 연산자 &lt; (목록) (STL/CLR)

비교 보다 작음 목록입니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value>
    bool operator<(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 컨테이너입니다.

*오른쪽*<br/>
비교할 오른쪽 컨테이너입니다.

### <a name="remarks"></a>설명

연산자 함수는 해당 하는 가장 낮은 위치에 대해서도 true를 반환 합니다 `i` `!(right[i] < left[i])` `left[i] < right[i]` . 그렇지 않은 경우이 메서드를 `left->size() < right->size()` 사용 하 여 두 목록을 요소 별로 비교할 때 *왼쪽* 이 *오른쪽* 에 정렬 되는지 여부를 테스트 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_operator_lt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="operatorlt-list-stlclr"></a><a name="op_lteq"></a> operator &lt; = (목록) (STL/CLR)

보다 작거나 같음 비교를 나열 합니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value>
    bool operator<=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 컨테이너입니다.

*오른쪽*<br/>
비교할 오른쪽 컨테이너입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `!(right < left)` . 이를 사용 하 여 두 목록을 요소 별로 비교할 때 *왼쪽* 이 *오른쪽* 다음에 정렬 되지 않는지 여부를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_list_operator_le.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="operator-list-stlclr"></a><a name="op_eq"></a> operator = = (목록) (STL/CLR)

동일한 비교를 나열 합니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value>
    bool operator==(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 컨테이너입니다.

*오른쪽*<br/>
비교할 오른쪽 컨테이너입니다.

### <a name="remarks"></a>설명

Operator 함수는 *left* 및 *right* 로 제어 되는 시퀀스의 길이가 같고 각 위치에 대해가 인 경우에만 true를 반환 합니다 `i` `left[i] ==` `right[i]` . 이를 사용 하 여 두 목록이 요소에 의해 비교 될 때 *왼쪽* 이 *오른쪽* 과 동일 하 게 정렬 되었는지 여부를 테스트 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_operator_eq.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="operatorgt-list-stlclr"></a><a name="op_gt"></a> 연산자 &gt; (목록) (STL/CLR)

비교 보다 큼을 나열 합니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value>
    bool operator>(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 컨테이너입니다.

*오른쪽*<br/>
비교할 오른쪽 컨테이너입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `right` `<` `left` . 이를 사용 하 여 두 목록을 요소 별로 비교할 때 *왼쪽* 이 *오른쪽* 다음에 정렬 되는지 여부를 테스트 합니다.

### <a name="example"></a>예제

```cpp
// cliext_list_operator_gt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="operatorgt-list-stlclr"></a><a name="op_gteq"></a> operator &gt; = (목록) (STL/CLR)

보다 크거나 같음 비교를 나열 합니다.

### <a name="syntax"></a>구문

```cpp
template<typename Value>
    bool operator>=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>매개 변수

*비어*<br/>
비교할 왼쪽 컨테이너입니다.

*오른쪽*<br/>
비교할 오른쪽 컨테이너입니다.

### <a name="remarks"></a>설명

연산자 함수는를 반환 합니다 `!(left` `<` `right)` . 이를 사용 하 여 두 목록을 요소 별로 비교할 때 *왼쪽* 이 *오른쪽* 앞에 정렬 되지 않는지 여부를 테스트할 수 있습니다.

### <a name="example"></a>예제

```cpp
// cliext_list_operator_ge.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```
