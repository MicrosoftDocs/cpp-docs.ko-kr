---
title: unique_ptr 클래스
ms.date: 11/04/2016
f1_keywords:
- memory/std::unique_ptr
- memory/std::unique_ptr::deleter_type
- memory/std::unique_ptr::element_type
- memory/std::unique_ptr::pointer
- memory/std::unique_ptr::get
- memory/std::unique_ptr::get_deleter
- memory/std::unique_ptr::release
- memory/std::unique_ptr::reset
- memory/std::unique_ptr::swap
helpviewer_keywords:
- std::unique_ptr [C++]
- std::unique_ptr [C++], deleter_type
- std::unique_ptr [C++], element_type
- std::unique_ptr [C++], pointer
- std::unique_ptr [C++], get
- std::unique_ptr [C++], get_deleter
- std::unique_ptr [C++], release
- std::unique_ptr [C++], reset
- std::unique_ptr [C++], swap
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
ms.openlocfilehash: b0751d7716e2f8587ab410e57c2bea17c5dd3e21
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520974"
---
# <a name="uniqueptr-class"></a>unique_ptr 클래스

소유한 개체 또는 배열에 대한 포인터를 저장합니다. 개체/배열은 다른 `unique_ptr`이 소유하지 않습니다. 개체/배열은 `unique_ptr`이 소멸될 때 소멸됩니다.

## <a name="syntax"></a>구문

```cpp
class unique_ptr {
public:
    unique_ptr();
    unique_ptr(nullptr_t Nptr);
    explicit unique_ptr(pointer Ptr);
    unique_ptr(pointer Ptr,
        typename conditional<is_reference<Del>::value, Del,
        typename add_reference<const Del>::type>::type Deleter);
    unique_ptr(pointer Ptr,
        typename remove_reference<Del>::type&& Deleter);
    unique_ptr(unique_ptr&& Right);
    template <class T2, Class Del2>
    unique_ptr(unique_ptr<T2, Del2>&& Right);
    unique_ptr(const unique_ptr& Right) = delete;
    unique_ptr& operator=(const unique_ptr& Right) = delete;
};

//Specialization for arrays:
template <class T, class D>
class unique_ptr<T[], D> {
public:
    typedef pointer;
    typedef T element_type;
    typedef D deleter_type;
    constexpr unique_ptr() noexcept;
    template <class U>
    explicit unique_ptr(U p) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    unique_ptr(unique_ptr&& u) noexcept;
    constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }     template <class U, class E>
        unique_ptr(unique_ptr<U, E>&& u) noexcept;
    ~unique_ptr();
    unique_ptr& operator=(unique_ptr&& u) noexcept;
    template <class U, class E>
    unique_ptr& operator=(unique_ptr<U, E>&& u) noexcept;
    unique_ptr& operator=(nullptr_t) noexcept;
    T& operator[](size_t i) const;

    pointer get() const noexcept;
    deleter_type& get_deleter() noexcept;
    const deleter_type& get_deleter() const noexcept;
    explicit operator bool() const noexcept;
    pointer release() noexcept;
    void reset(pointer p = pointer()) noexcept;
    void reset(nullptr_t = nullptr) noexcept;
    template <class U>
    void reset(U p) noexcept = delete;
    void swap(unique_ptr& u) noexcept;  // disable copy from lvalue unique_ptr(const unique_ptr&) = delete;
    unique_ptr& operator=(const unique_ptr&) = delete;
};
```

### <a name="parameters"></a>매개 변수

*오른쪽*<br/>
`unique_ptr`

*Nptr*<br/>
`rvalue` 형식의 `std::nullptr_t`입니다.

*ptr*<br/>
`pointer`

*삭제 자*<br/>
`deleter`에 바인딩되는 `unique_ptr` 함수.

## <a name="exceptions"></a>예외

`unique_ptr`에는 예외가 생성되지 않았습니다.

## <a name="remarks"></a>설명

`unique_ptr` 클래스는 `auto_ptr`을 대체하며 C++ 표준 라이브러리 컨테이너의 요소로 사용할 수 있습니다.

`unique_ptr`의 새 인스턴스를 효율적으로 만들려면 [make_unique](../standard-library/memory-functions.md#make_unique) 도우미 함수를 사용하세요.

`unique_ptr`은 리소스를 고유하게 관리합니다. 각 `unique_ptr` 개체는 null 포인터를 소유 또는 저장하는 개체에 대해 포인터를 저장합니다. 리소스는 둘 이상의 `unique_ptr` 개체가 소유할 수 없으며, 특정 리소스를 소유하는 `unique_ptr` 개체가 제거되면 리소스가 해제됩니다. `unique_ptr` 개체는 이동할 수 있지만 복사할 수는 없습니다. 자세한 내용은 [Rvalue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 참조하세요.

리소스는 특정 `deleter`에 대해 리소스가 할당된 방식을 알고 있는 `Del` 형식의 저장된 `unique_ptr` 개체를 호출하여 해제됩니다. 기본값 `deleter` `default_delete<T>` 리소스에서 가리키는 가정 `ptr` 할당 된 `new`, 및 호출 하 여 해제할 수는 `delete _Ptr`합니다. (부분 특수화 `unique_ptr<T[]>`는 `new[]`로 할당된 배열 개체를 관리하며, delete[] `deleter`을 호출하는 데 전문화된 기본 `default_delete<T[]>``ptr`이 있습니다.)

소유한 리소스에 대한 저장된 포인터, `stored_ptr`에는 `pointer`가 있습니다. 정의된 경우 `Del::pointer`이고, 정의되지 않은 경우 `T *`입니다. `deleter`가 상태 비저장일 경우 저장된 `stored_deleter` 개체 `deleter`는 개체에서 공간을 차지하지 않습니다. `Del`는 참조 형식이 될 수 있습니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[unique_ptr](#unique_ptr)|`unique_ptr`의 8가지 생성자가 있습니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[deleter_type](#deleter_type)|템플릿 매개 변수 `Del`의 동의어.|
|[element_type](#element_type)|템플릿 매개 변수 `T`의 동의어.|
|[pointer](#pointer)|`Del::pointer`의 동의어(정의된 경우)이며 그렇지 않은 경우 `T *`.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[get](#get)|`stored_ptr`를 반환합니다.|
|[get_deleter](#get_deleter)|`stored_deleter`에 대한 참조를 반환합니다.|
|[release](#release)|`pointer()`에 `stored_ptr`를 반환하고 이전 내용을 반환합니다.|
|[reset](#reset)|현재 소유한 리소스를 해제하고 새 리소스를 허용합니다.|
|[swap](#swap)|리소스를 교환하고 `deleter`를 제공된 `unique_ptr`로 교환합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|**operator bool**|로 변환할 수 있는 형식의 값을 반환 하는 연산자 **bool**합니다. 변환의 결과 **bool** 됩니다 **true** 때 `get() != pointer()`고, 그렇지 않으면 **false**합니다.|
|`operator->`|멤버 함수는 `stored_ptr`를 반환합니다.|
|`operator*`|멤버 함수는 `*stored_ptr`를 반환합니다.|
|[unique_ptr operator=](#unique_ptr_operator_eq)|`unique_ptr` 또는 `pointer-type`의 값을 현재 `unique_ptr`에 할당합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<memory>

**네임스페이스:** std

## <a name="deleter_type"></a>  deleter_type

이 형식은 템플릿 매개 변수 `Del`의 동의어입니다.

```cpp
typedef Del deleter_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Del`의 동의어입니다.

## <a name="element_type"></a>  element_type

이 형식은 템플릿 매개 변수 `Type`의 동의어입니다.

```cpp
typedef Type element_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `Ty`의 동의어입니다.

## <a name="get"></a>  unique_ptr::get

`stored_ptr`를 반환합니다.

```cpp
pointer get() const;
```

### <a name="remarks"></a>설명

멤버 함수는 `stored_ptr`를 반환합니다.

## <a name="get_deleter"></a>  unique_ptr::get_deleter

`stored_deleter`에 대한 참조를 반환합니다.

```cpp
Del& get_deleter();

const Del& get_deleter() const;
```

### <a name="remarks"></a>설명

멤버 함수는 `stored_deleter`에 대한 참조를 반환합니다.

## <a name="unique_ptr_operator_eq"></a>  unique_ptr operator=

제공된 `unique_ptr`의 주소를 현재 항목에 할당합니다.

```cpp
unique_ptr& operator=(unique_ptr&& right);
template <class U, Class Del2>
unique_ptr& operator=(unique_ptr<Type, Del>&& right);
unique_ptr& operator=(pointer-type);
```

### <a name="parameters"></a>매개 변수

현재 `unique_ptr`의 값을 할당하는 데 사용된 `unique_ptr` 참조입니다.

### <a name="remarks"></a>설명

구성원 함수는 `reset(right.release())`를 호출하고 `right.stored_deleter`를 `stored_deleter`로 이동한 다음 `*this`를 반환합니다.

## <a name="pointer"></a>  pointer

`Del::pointer`의 동의어(정의된 경우)이며 그렇지 않은 경우 `Type *`.

```cpp
typedef T1 pointer;
```

### <a name="remarks"></a>설명

형식은 `Del::pointer`의 동의어(정의된 경우)이며 그렇지 않은 경우 `Type *`입니다.

## <a name="release"></a>  unique_ptr::release

호출자에 게 반환 되는 저장 된 포인터의 소유권을 해제 하 고 저장 된 포인터 값을 설정 합니다 **nullptr**합니다.

```cpp
pointer release();
```

### <a name="remarks"></a>설명

`release`를 사용하여 `unique_ptr`이 저장한 원시 포인터의 소유권을 가져올 수 있습니다. 호출자는 반환된 포인터를 삭제해야 합니다. `unique-ptr`은 비어 있는 기본 생성 상태로 설정됩니다. `unique_ptr` 호출 후에 호환되는 형식의 다른 포인터를 `release`에 할당할 수 있습니다.

### <a name="example"></a>예제

이 예에서는 릴리스의 호출자가 반환된 개체를 책임지는 방식을 보여 줍니다.

```cpp
// stl_release_unique.cpp
// Compile by using: cl /W4 /EHsc stl_release_unique.cpp
#include <iostream>
#include <memory>

struct Sample {
   int content_;
   Sample(int content) : content_(content) {
      std::cout << "Constructing Sample(" << content_ << ")" << std::endl;
   }
   ~Sample() {
      std::cout << "Deleting Sample(" << content_ << ")" << std::endl;
   }
};

void ReleaseUniquePointer() {
   // Use make_unique function when possible.
   auto up1 = std::make_unique<Sample>(3);
   auto up2 = std::make_unique<Sample>(42);

   // Take over ownership from the unique_ptr up2 by using release
   auto ptr = up2.release();
   if (up2) {
      // This statement does not execute, because up2 is empty.
      std::cout << "up2 is not empty." << std::endl;
   }
   // We are now responsible for deletion of ptr.
   delete ptr;
   // up1 deletes its stored pointer when it goes out of scope.
}

int main() {
   ReleaseUniquePointer();
}
```

컴퓨터 출력:

```Output
Constructing Sample(3)
Constructing Sample(42)
Deleting Sample(42)
Deleting Sample(3)
```

## <a name="reset"></a>  unique_ptr::reset

포인터 매개 변수의 소유권을 가져온 후 원래 저장된 포인터를 삭제합니다. 새 포인터가 원래 저장 된 포인터를 동일 `reset` 포인터를 삭제 하 고 저장 된 포인터를 설정 **nullptr**합니다.

```cpp
void reset(pointer ptr = pointer());
void reset(nullptr_t ptr);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*ptr*|소유권을 가져올 리소스에 대한 포인터입니다.|

### <a name="remarks"></a>설명

사용 하 여 `reset` 저장 된 변경 [포인터](#pointer) 소유 하는 `unique_ptr` 에 *ptr* 다음 원래 저장 된 포인터를 삭제 합니다. `unique_ptr`이 비어 있지 않으면 `reset`은 원래 저장된 포인터에서 [get_deleter](#get_deleter)가 반환하는 deleter 함수를 호출합니다.

때문에 `reset` 먼저 새 포인터를 저장 *ptr*, 다음 원래 저장 된 포인터를 삭제 하 고 있기 `reset` 를 즉시 삭제할 *ptr* 원본과 같은 경우 저장 된 포인터입니다.

## <a name="swap"></a>  unique_ptr::swap

두 `unique_ptr` 개체 간에 포인터를 교환합니다.

```cpp
void swap(unique_ptr& right);
```

### <a name="parameters"></a>매개 변수

*right*<br/>
포인터를 교환하는 데 사용되는 `unique_ptr`입니다.

### <a name="remarks"></a>설명

멤버 함수는 `stored_ptr`을 `right.stored_ptr`로 교환하고 `stored_deleter`를 `right.stored_deleter`로 교환합니다.

## <a name="unique_ptr"></a>  unique_ptr::unique_ptr

`unique_ptr`의 8가지 생성자가 있습니다.

```cpp
unique_ptr();

unique_ptr(nullptr_t);
explicit unique_ptr(pointer ptr);

unique_ptr(
    Type* ptr,
    typename conditional<
    is_reference<Del>::value,
    Del,
    typename add_reference<const Del>::type>::type _Deleter);

unique_ptr(pointer ptr, typename remove_reference<Del>::type&& _Deleter);
unique_ptr(unique_ptr&& right);
template <class Ty2, Class Del2>
unique_ptr(unique_ptr<Ty2, Del2>&& right);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*ptr*|`unique_ptr.`에 할당할 리소스에 대한 포인터입니다.|
|*_Deleter*|`unique_ptr`에 할당할 `deleter`입니다.|
|*right*|`unique_ptr` 필드가 새로 생성된 `unique_ptr`에 이동 할당되는 `unique_ptr`에 대한 `rvalue reference`입니다.|

### <a name="remarks"></a>설명

처음 두 생성자가 리소스를 관리하지 않는 개체를 생성합니다. 세 번째 생성자 저장소 *ptr* 에서 `stored_ptr`합니다. 네 번째 생성자 저장소 *ptr* 에 `stored_ptr` 하 고 `deleter` 에서 `stored_deleter`합니다.

다섯 번째 생성자 저장소 *ptr* 에 `stored_ptr` 이동 `deleter` 에 `stored_deleter`입니다. 여섯 번째와 일곱 번째 생성자는 `right.release()`을 `stored_ptr`에 저장하고 `right.get_deleter()`을 `stored_deleter`로 이동합니다.

## <a name="dtorunique_ptr"></a>  unique_ptr ~unique_ptr

`unique_ptr`에 대한 소멸자는 `unique_ptr` 개체를 삭제합니다.

```cpp
~unique_ptr();
```

### <a name="remarks"></a>설명

이 소멸자는 `get_deleter()(stored_ptr)`을 호출합니다.

## <a name="see-also"></a>참고자료

[\<memory>](../standard-library/memory.md)<br/>
