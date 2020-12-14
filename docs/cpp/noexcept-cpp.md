---
description: '자세히 알아보기: noexcept (c + +)'
title: noexcept(C++)
ms.date: 11/19/2019
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: ca4abfc48e3850f014c29cea2fd9108f7b556072
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223726"
---
# <a name="noexcept-c"></a>noexcept(C++)

**C + + 11:** 함수에서 예외를 throw 할 수 있는지 여부를 지정 합니다.

## <a name="syntax"></a>Syntax

> *noexcept*: \
> &nbsp;&nbsp;&nbsp;&nbsp;**`noexcept`**\
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept (** *상수 식* **)**

### <a name="parameters"></a>매개 변수

*constant-expression*<br/>
**`bool`** 잠재적 예외 형식 집합이 비어 있는지 여부를 나타내는 형식의 상수 식입니다. 비 조건부 버전은와 동일 `noexcept(true)` 합니다.

## <a name="remarks"></a>설명

*Noexcept 식은* 함수를 종료 하는 모든 예외에 대 한 예외 처리기에 의해 일치 될 수 있는 형식 집합을 나타내는 함수 선언에 대 한 접미사 인 *예외 사양의* 일종입니다. 단항 조건 연산자 `noexcept(` *constant_expression* `)` *constant_expression* 를 생성 하 **`true`** 고, 무조건 동의어는 **`noexcept`** 함수를 종료할 수 있는 잠재적인 예외 형식 집합이 비어 있음을 지정 합니다. 즉, 함수는 예외를 throw 하지 않으며 예외를 범위 외부에서 전파 하지 않습니다. 연산자 constant_expression `noexcept(` *constant_expression* `)` 소멸자  또는 할당 취소 함수를 제외 하 고 예외 사양이 없는 경우 **`false`** 함수를 종료할 수 있는 잠재적인 예외 집합이 모든 형식의 집합 임을 나타냅니다.

**`noexcept`** 직접 또는 간접적으로 호출 하는 모든 함수가 또는 인 경우에만 함수를로 표시 **`noexcept`** **`const`** 합니다. 컴파일러는 함수에 대해 버블링 될 수 있는 예외에 대 한 모든 코드 경로를 반드시 확인 하지는 않습니다 **`noexcept`** . 예외로 표시 된 함수의 외부 범위를 종료 하는 경우에 **`noexcept`** 는 [std:: terminate](../standard-library/exception-functions.md#terminate) 가 즉시 호출 되며 범위 내 개체의 소멸자가 호출 된다는 보장이 없습니다. **`noexcept`** `throw()` 이제 표준에서 더 이상 사용 되지 않는 동적 예외 지정자 대신을 사용 합니다. **`noexcept`** 예외가 호출 스택을 전파 하지 않도록 허용 하는 모든 함수에 적용 하는 것이 좋습니다. 함수가 선언 되 면 **`noexcept`** 컴파일러는 여러 컨텍스트에서 더 효율적인 코드를 생성할 수 있습니다. 자세한 내용은 [예외 사양](exception-specifications-throw-cpp.md)을 참조 하세요.

## <a name="example"></a>예제

해당 인수를 복사 하는 템플릿 함수는 **`noexcept`** 복사 중인 개체가 일반 이전 데이터 형식 (POD) 인 조건에 선언 될 수 있습니다. 이러한 함수는 다음과 같이 선언될 수 있습니다.

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>참고 항목

[예외 및 오류 처리에 대 한 최신 c + + 모범 사례](errors-and-exception-handling-modern-cpp.md)<br/>
[예외 사양 (throw, noexcept)](exception-specifications-throw-cpp.md)
