---
title: initializer_list 클래스
description: Visual Studio에서 Microsoft에 의해 구현 되는 c + + 표준 라이브러리의 initializer_list 클래스에 대 한 참조입니다.
ms.date: 01/28/2020
f1_keywords:
- initializer_list/std::initializer_list::initializer_list
- initializer_list/std::initializer_list::begin
- initializer_list/std::initializer_list::end
- initializer_list/std::initializer_list::size
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
helpviewer_keywords:
- std::initializer_list::initializer_list
- std::initializer_list::begin
- std::initializer_list::end
- std::initializer_list::size
ms.openlocfilehash: 232855fbcac1e4df9af7cf956fda80201326a401
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504633"
---
# <a name="initializer_list-class"></a>initializer_list 클래스

각 멤버가 지정된 형식인 요소 배열에 대한 액세스를 제공합니다.

## <a name="syntax"></a>구문

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>매개 변수

*입력할*\
`initializer_list`에 저장되는 요소 데이터 형식입니다.

## <a name="remarks"></a>설명

중괄호로 묶인 이니셜라이저 목록을 사용하여 `initializer_list`를 생성할 수 있습니다.

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

컴파일러는 함수 서명에 `initializer_list`가 필요할 때마다 같은 요소가 포함된 중괄호로 묶인 이니셜라이저 목록을 `initializer_list`로 변환합니다. 사용에 대 한 자세한 내용은 `initializer_list` [균일 초기화 및 생성자 위임](../cpp/initializing-classes-and-structs-without-constructors-cpp.md) 을 참조 하세요.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[initializer_list](#initializer_list)|`initializer_list` 형식의 개체를 생성합니다.|

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|`value_type`|`initializer_list` 요소의 형식입니다.|
|`reference`|`initializer_list`의 요소에 대한 참조를 제공하는 형식입니다.|
|`const_reference`|`initializer_list`의 요소에 대한 상수 참조를 제공하는 형식입니다.|
|`size_type`|`initializer_list`의 요소 수를 나타내는 형식입니다.|
|`iterator`|`initializer_list`에 대한 반복기를 제공하는 형식입니다.|
|`const_iterator`|`initializer_list`에 대한 상수 반복기를 제공하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[시작](#begin)|`initializer_list`의 첫 번째 요소에 대한 포인터를 반환합니다.|
|[end](#end)|`initializer_list`의 마지막 요소를 지난 다음 요소에 대한 포인터를 반환합니다.|
|[size](#size)|`initializer_list`에 있는 요소 수를 반환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<initializer_list>

**네임스페이스:** std

## <a name="initializer_listbegin"></a><a name="begin"></a> initializer_list:: begin

`initializer_list`의 첫 번째 요소에 대한 포인터를 반환합니다.

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>반환 값

`initializer_list`의 첫 번째 요소에 대한 포인터입니다. 목록이 비어 있는 경우 목록의 시작과 끝에 대한 포인터가 동일합니다.

## <a name="initializer_listend"></a><a name="end"></a> initializer_list:: end

`initializer list`의 마지막 요소를 지난 다음 요소에 대한 포인터를 반환합니다.

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>반환 값

목록의 마지막 요소를 지난 다음 요소에 대한 포인터입니다. 목록이 비어 있으면 목록의 첫 번째 요소에 대 한 포인터와 동일 합니다.

## <a name="initializer_listinitializer_list"></a><a name="initializer_list"></a> initializer_list:: initializer_list

`initializer_list` 형식의 개체를 생성합니다.

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>매개 변수

*기본*\
복사할 요소의 범위에서 첫 번째 요소의 위치입니다.

*최신*\
복사할 요소의 범위를 벗어나는 첫 번째 요소의 위치입니다.

### <a name="remarks"></a>설명

`initializer_list`는 지정된 형식의 개체 배열을 기반으로 합니다. 를 복사 하면 `initializer_list` 동일한 개체를 가리키는 목록의 두 번째 인스턴스가 생성 되 고 기본 개체는 복사 되지 않습니다.

### <a name="example"></a>예제

```cpp
// initializer_list_class.cpp
// compile with: /EHsc
#include <initializer_list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty initializer_list c0
    initializer_list <int> c0;

    // Create an initializer_list c1 with 1 element
    initializer_list <int> c1{ 3 };

    // Create an initializer_list c2 with 5 elements
    initializer_list <int> c2{ 5, 4, 3, 2, 1 };

    // Create a copy, initializer_list c3, of initializer_list c2
    initializer_list <int> c3(c2);

    // Create a initializer_list c4 by copying the range c3[ first,  last)
    const int* c3_ptr = c3.begin();
    c3_ptr++;
    c3_ptr++;
    initializer_list <int> c4(c3.begin(), c3_ptr);

    // Move initializer_list c4 to initializer_list c5
    initializer_list <int> c5(move(c4));

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 3
c2 = 5 4 3 2 1
c3 = 5 4 3 2 1
c5 = 5 4
```

## <a name="initializer_listsize"></a><a name="size"></a> initializer_list:: size

목록에 있는 요소 수를 반환합니다.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>반환 값

목록에 있는 요소의 수입니다.

## <a name="see-also"></a>참고 항목

[<forward_list>](../standard-library/forward-list.md)
