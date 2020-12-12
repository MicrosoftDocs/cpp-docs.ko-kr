---
description: Add_rvalue_reference 클래스에 대해 자세히 알아보세요.
title: add_rvalue_reference 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_rvalue_reference
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
ms.openlocfilehash: f4f5b58ddd2aa1e02b3023a27ef2feba83624326
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319884"
---
# <a name="add_rvalue_reference-class"></a>add_rvalue_reference 클래스

개체 또는 함수 형식인 경우 템플릿 매개 변수의 rvalue 참조 형식을 만듭니다. 아닌 경우, 참조 축소에 대한 의미 체계 때문에 형식이 템플릿 매개 변수와 동일합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>매개 변수

*트*\
수정할 형식입니다.

## <a name="remarks"></a>설명

클래스에는 `add_rvalue_reference` `type` 템플릿 매개 변수 *T* 에 대 한 rvalue 참조 형식의 별칭인 라는 멤버가 있습니다. 참조 축소의 의미 체계는 비 개체 및 비 함수 형식 *t* 의 경우 t `T&&` 가 *t* 임을 의미 합니다. 예를 들어 *T* 가 lvalue 참조 형식이 면 `add_rvalue_reference<T>::type` 는 rvalue 참조가 아닌 lvalue 참조 형식입니다.

편의상는 \<type_traits> 의 멤버를 별칭으로 하는 도우미 템플릿를 정의 `add_rvalue_reference_t` `type` `add_rvalue_reference` 합니다.

## <a name="example"></a>예제

static_assert를 사용하는 이 코드 예제에서는 `add_rvalue_reference` 및 `add_rvalue_reference_t`를 사용하여 rvalue 참조 형식을 만드는 방법과 lvalue 참조 형식에 대한 `add_rvalue_reference`의 결과가 rvalue 참조가 아닌 lvalue 참조 형식으로 축소되는 방법을 보여 줍니다.

```cpp
// ex_add_rvalue_reference.cpp
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp
#include <type_traits>
#include <iostream>
#include <string>

using namespace std;
int main()
{
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,
        "Expected add_rvalue_reference_t<string> to be string&&");
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,
        "Expected add_rvalue_reference_t<string*> to be string*&&");
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,
        "Expected add_rvalue_reference_t<string&> to be string&");
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,
        "Expected add_rvalue_reference_t<string&&> to be string&&");
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;
    return 0;
}

/*Output:
All static_assert tests of add_rvalue_reference passed.
*/
```

## <a name="requirements"></a>요구 사항

헤더: \<type_traits>

네임스페이스: std

## <a name="see-also"></a>참고 항목

[<type_traits>](type-traits.md)\
[add_lvalue_reference 클래스](add-lvalue-reference-class.md)\
[is_rvalue_reference 클래스](is-rvalue-reference-class.md)
