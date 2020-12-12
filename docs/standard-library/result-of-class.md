---
description: Result_of 클래스에 대해 자세히 알아보세요.
title: result_of 클래스
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
ms.openlocfilehash: 2aba6b073309be064b9ff0edc7bffa4d8d0098e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273906"
---
# <a name="result_of-class"></a>result_of 클래스

지정된 인수 유형을 사용하는 호출 가능 형식의 반환 형식을 결정합니다. C + + 14에서 추가 되었고, c + + 17에서 사용 되지 않습니다.

## <a name="syntax"></a>구문

```cpp
template<class>
struct result_of; // Causes a static assert

template <class Fn, class... ArgTypes>
struct result_of<Fn(ArgTypes...)>;

// Helper type
template<class T>
   using result_of_t = typename result_of<T>::type;
```

### <a name="parameters"></a>매개 변수

*Fn*\
쿼리할 호출 가능 형식입니다.

*ArgTypes*\
쿼리할 호출 가능 형식에 대한 인수 목록의 형식입니다.

## <a name="remarks"></a>설명

이 템플릿을 사용 하 여 컴파일 타임에 ()의 결과 형식을 확인할 수 `Fn` `ArgTypes` 있습니다. 여기서 *Fn* 은 호출 가능 형식, 함수에 대 한 참조 또는 호출 가능 형식에 대 한 참조 이거나 *argtypes* 에서 형식의 인수 목록을 사용 하 여 호출 됩니다. `type`클래스 템플릿의 멤버는 확인 `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` 되지 않은 식이 올바른 형식인 경우 결과 형식의 이름을 `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` 로 합니다. 그렇지 않으면 클래스 템플릿에 멤버가 없습니다 `type` . 매개 변수 팩 *argtypes* 의 형식 *Fn* 및 모든 형식은 완전 한 형식, **`void`** 또는 범위를 알 수 없는 배열 이어야 합니다. C + + 17의 [invoke_result](invoke-result-class.md) 에는 더 이상 사용 되지 않습니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[invoke_result 클래스](invoke-result-class.md)
