---
description: Add_cv 클래스에 대해 자세히 알아보세요.
title: add_cv 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_cv
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
ms.openlocfilehash: bc25efd879a27b3d3af2e5f4db8dd74fafa3fb45
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319933"
---
# <a name="add_cv-class"></a>add_cv 클래스

형식 **`const volatile`** 에서 형식을 만듭니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct add_cv;

template <class T>
using add_cv_t = typename add_cv<T>::type;
```

### <a name="parameters"></a>매개 변수

*트*\
수정할 형식입니다.

## <a name="remarks"></a>설명

`add_cv<T>` `type` **`typedef`** *T* 가 이미 cv 한정자를가지고 있거나 참조 이거나 함수인  경우를 제외 하 고, 수정 된 형식의 인스턴스에는 [add_volatile](add-volatile-class.md) 및 [add_const](add-const-class.md)에 의해 수정 된 동일한 멤버가 있습니다.

`add_cv_t<T>` 도우미 형식은 `add_cv<T>` 멤버 typedef `type`에 액세스하기 위한 바로 가기입니다.

## <a name="example"></a>예제

```cpp
// add_cv.cpp
// compile by using: cl /EHsc /W4 add_cv.cpp
#include <type_traits>
#include <iostream>

struct S {
    void f() {
        std::cout << "invoked non-cv-qualified S.f()" << std::endl;
    }
    void f() const {
        std::cout << "invoked const S.f()" << std::endl;
    }
    void f() volatile {
        std::cout << "invoked volatile S.f()" << std::endl;
    }
    void f() const volatile {
        std::cout << "invoked const volatile S.f()" << std::endl;
    }
};

template <class T>
void invoke() {
    T t;
    ((T *)&t)->f();
}

int main()
{
    invoke<S>();
    invoke<std::add_const<S>::type>();
    invoke<std::add_volatile<S>::type>();
    invoke<std::add_cv<S>::type>();
}
```

```Output
invoked non-cv-qualified S.f()
invoked const S.f()
invoked volatile S.f()
invoked const volatile S.f()
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](type-traits.md)\
[remove_const 클래스](remove-const-class.md)\
[remove_volatile 클래스](remove-volatile-class.md)
