---
description: '&lt;Type_traits 함수에 대해 자세히 알아보세요. &gt;'
title: '&lt;type_traits&gt; 함수'
ms.date: 11/04/2016
ms.assetid: dce4492f-f3e4-4d5e-bdb4-5875321254ec
helpviewer_keywords:
- std::is_assignable
- std::is_copy_assignable
- std::is_copy_constructible
- std::is_default_constructible
- std::is_move_assignable
- std::is_move_constructible
- std::is_nothrow_move_assignable
- std::is_trivially_copy_assignable
- std::is_trivially_move_assignable
- std::is_trivially_move_constructible
ms.openlocfilehash: a1608ddc9d846ca9e8e851ef67d390aebb6f840e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253327"
---
# <a name="lttype_traitsgt-functions"></a>&lt;type_traits&gt; 함수

[is_assignable](#is_assignable)\
[is_copy_assignable](#is_copy_assignable)\
[is_copy_constructible](#is_copy_constructible)\
[is_default_constructible](#is_default_constructible)\
[is_move_assignable](#is_move_assignable)\
[is_move_constructible](#is_move_constructible)\
[is_nothrow_move_assignable](#is_nothrow_move_assignable)\
[is_nothrow_swappable](#is_nothrow_swappable)\
[is_nothrow_swappable_with](#is_nothrow_swappable_with)\
[is_swappable](#is_swappable)\
[is_swappable_with](#is_swappable_with)\
[is_trivially_copy_assignable](#is_trivially_copy_assignable)\
[is_trivially_move_assignable](#is_trivially_move_assignable)\
[is_trivially_move_constructible](#is_trivially_move_constructible)

## <a name="is_assignable"></a><a name="is_assignable"></a> is_assignable

형식 *에서* 값을 형식에 할당할 수 있는지 *여부를 테스트* 합니다.

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>매개 변수

*받는 사람*\
할당을 받는 개체의 형식입니다.

*보낸 사람*\
값을 제공하는 개체의 형식입니다.

### <a name="remarks"></a>설명

평가되지 않은 `declval<To>() = declval<From>()` 식은 올바른 형식이어야 합니다. 및 *둘 다 완전 한 형식* ,  **`void`** 또는 범위를 알 수 없는 배열 이어야 합니다.

## <a name="is_copy_assignable"></a><a name="is_copy_assignable"></a> is_copy_assignable

할당 시 형식을 복사할 수 있는지 여부를 테스트합니다.

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

### <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식이 복사 할당 연산자를 가진 클래스인 경우 true이 고 그렇지 않은 경우 false입니다. Is_assignable와 동일 \<Ty&, const Ty&> 합니다.

## <a name="is_copy_constructible"></a><a name="is_copy_constructible"></a> is_copy_constructible

형식에 복사 생성자가 있는지 테스트합니다.

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

### <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식이 복사 생성자가 있는 클래스인 경우 true이 고 그렇지 않은 경우 false입니다.

### <a name="example"></a>예제

```cpp
#include <type_traits>
#include <iostream>

struct Copyable
{
    int val;
};

struct NotCopyable
{
   NotCopyable(const NotCopyable&) = delete;
   int val;

};

int main()
{
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha
        << std::is_copy_constructible<Copyable>::value << std::endl;
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha
        << std::is_copy_constructible<NotCopyable>::value << std::endl;

    return (0);
}
```

```Output
is_copy_constructible<Copyable> == true
is_copy_constructible<NotCopyable > == false
```

## <a name="is_default_constructible"></a><a name="is_default_constructible"></a> is_default_constructible

형식에 기본 생성자가 있는지 테스트합니다.

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

### <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *T* 형식이 기본 생성자가 있는 클래스 형식인 경우 true이 고 그렇지 않은 경우 false입니다. 이것은 조건자 `is_constructible<T>`에 해당합니다. *T* 형식은 완전 한 형식, **`void`** 또는 범위를 알 수 없는 배열 이어야 합니다.

### <a name="example"></a>예제

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}
```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="is_move_assignable"></a><a name="is_move_assignable"></a> is_move_assignable

형식을 이동 할당할 수 있는지 테스트합니다.

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

### <a name="remarks"></a>설명

형식에 대한 rvalue 참조를 형식에 대한 참조에 할당할 수 있는 경우 형식은 이동 할당할 수 있습니다. 형식 조건자는 `is_assignable<T&, T&&>`와 같습니다. 이동 할당 가능한 형식에는 컴파일러에서 생성되었거나 사용자가 정의한 이동 할당 연산자를 포함하는 참조 가능한 스칼라 형식과 클래스 형식이 포함됩니다.

## <a name="is_move_constructible"></a><a name="is_move_constructible"></a> is_move_constructible

형식에 이동 생성자가 있는지 테스트합니다.

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>매개 변수

*트*\
평가할 형식입니다.

### <a name="remarks"></a>설명

이동 작업을 사용 하 여 *T* 형식을 생성할 수 있는 경우 true로 평가 되는 형식 조건자입니다. 이 조건자는 `is_constructible<T, T&&>`와 같습니다.

## <a name="is_nothrow_move_assignable"></a><a name="is_nothrow_move_assignable"></a> is_nothrow_move_assignable

형식에 **`nothrow`** 이동 할당 연산자가 있는지 테스트 합니다.

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

### <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식에 nothrow 이동 할당 연산자가 있는 경우 true이 고 그렇지 않은 경우 false입니다.

## <a name="is_nothrow_swappable"></a><a name="is_nothrow_swappable"></a> is_nothrow_swappable

```cpp
template <class T> struct is_nothrow_swappable;
```

## <a name="is_nothrow_swappable_with"></a><a name="is_nothrow_swappable_with"></a> is_nothrow_swappable_with

```cpp
template <class T, class U> struct is_nothrow_swappable_with;
```

## <a name="is_swappable"></a><a name="is_swappable"></a> is_swappable

```cpp
template <class T> struct is_swappable;
```

## <a name="is_swappable_with"></a><a name="is_swappable_with"></a> is_swappable_with

```cpp
template <class T, class U> struct is_swappable_with;
```

## <a name="is_trivially_copy_assignable"></a><a name="is_trivially_copy_assignable"></a> is_trivially_copy_assignable

형식에 Trivial 복사 할당 연산자가 있는지 여부를 테스트합니다.

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

### <a name="remarks"></a>설명

형식 조건자의 인스턴스는 형식 *T* 가 trivial 복사 할당 연산자를 가진 클래스인 경우 true이 고 그렇지 않은 경우 false입니다.

클래스 *t* 에 대 한 할당 생성자는 암시적으로 제공 되 고, 클래스 *t* 에 가상 함수가 없고, 클래스 t에 가상 베이스가 없고, 클래스 *t* 형식의 모든 비정적 데이터 멤버의 클래스에 trivial 대입 연산자가 있으며, 클래스 배열 형식의 모든 비정적 데이터 멤버의 클래스에 trivial 대입 연산자가 있는 경우 trivial입니다.

## <a name="is_trivially_move_assignable"></a><a name="is_trivially_move_assignable"></a> is_trivially_move_assignable

형식에 trivial 이동 할당 연산자가 있는지 여부를 테스트합니다.

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

### <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식이 trivial 이동 할당 연산자를 가진 클래스인 경우 true이 고 그렇지 않은 경우 false입니다.

클래스에 대 한 이동 할당 연산자 *는 다음과* 같은 경우 trivial입니다.

암시적으로 제공된 경우

*Ty* 클래스에 가상 함수가 없습니다.

*Ty* 클래스에 가상 기본이 없습니다.

클래스 형식의 모든 비정적 데이터 멤버의 클래스에 trivial 이동 할당 연산자가 있는 경우

클래스 형식 배열의 모든 비정적 데이터 멤버의 클래스에 trivial 이동 할당 연산자가 있는 경우

## <a name="is_trivially_move_constructible"></a><a name="is_trivially_move_constructible"></a> is_trivially_move_constructible

형식에 Trivial 이동 생성자가 있는지 여부를 테스트합니다.

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

### <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *Ty* 형식이 trivial 이동 생성자가 있는 클래스인 경우 true이 고 그렇지 않은 경우 false입니다.

*클래스의 이동 생성자는 다음과* 같은 경우 trivial입니다.

암시적으로 선언된 경우

매개 변수 형식이 암시적 선언의 형식과 동일한 경우

*Ty* 클래스에 가상 함수가 없습니다.

*Ty* 클래스에 가상 기본이 없습니다.

클래스에 휘발성 비정적 데이터 멤버가 없는 경우

클래스의 모든 직접 *기본에 trivial* 이동 생성자가 있습니다.

클래스 형식의 모든 비정적 데이터 멤버의 클래스에 Trivial 이동 생성자가 있는 경우

클래스 배열 형식의 모든 비정적 데이터 멤버의 클래스에 Trivial 이동 생성자가 있는 경우

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
