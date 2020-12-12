---
description: Invoke_result 클래스에 대해 자세히 알아보세요.
title: invoke_result 클래스
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: 4204ff1b0b8d38eab4b7d8c0de4709b90e12f5d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231499"
---
# <a name="invoke_result-class"></a>invoke_result 클래스

컴파일 타임에 지정 된 인수 형식을 사용 하는 호출 가능 형식의 반환 형식을 결정 합니다. C + + 17에 추가 되었습니다.

## <a name="syntax"></a>구문

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<class Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>매개 변수

*호출*\
쿼리할 호출 가능 형식입니다.

*Args*\
쿼리할 호출 가능 형식에 대한 인수 목록의 형식입니다.

## <a name="remarks"></a>설명

이 템플릿을 사용 하 여 컴파일 시간 *에 호출할 수 있는 (**args*...)의 결과 형식을 확인할 수 있습니다. 여기에서 *호출 가능* 하 고 *args* 의 모든 형식은 완전 한 형식, 알 수 없는 범위 배열 또는 cv 한정이 될 수 **`void`** 있습니다. `type`클래스 템플릿의 멤버는 인수 인수를 사용 하 여 호출할 때 호출 *가능* 의 반환 형식을 이름으로 사용 *합니다.* `type`인수 인수를 사용 하 여 호출할 때 *호출 될* 수 있는 경우에만 멤버가 정의 됩니다 *.* 확인 되지 않은 컨텍스트에서 그렇지 않은 경우 클래스 템플릿에는 `type` 컴파일 타임에 특정 인수 형식 집합에 대 한 SFINAE 테스트를 허용 하는 멤버가 없습니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
