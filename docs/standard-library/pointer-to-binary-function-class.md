---
description: Pointer_to_binary_function 클래스에 대해 자세히 알아보세요.
title: pointer_to_binary_function 클래스
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_binary
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
ms.openlocfilehash: 5cdecc297ff5c55c9b6c57b5b6ab029636f3958c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340712"
---
# <a name="pointer_to_binary_function-class"></a>pointer_to_binary_function 클래스

이항 함수 포인터를 조정 가능한 이항 함수로 변환합니다. C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다.

## <a name="syntax"></a>구문

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>매개 변수

*pfunc*\
변환할 이진 함수입니다.

*비어*\
*\* Pfunc* 가 호출 되는 왼쪽 개체입니다.

*오른쪽*\
*\* Pfunc* 가 호출 되는 오른쪽 개체입니다.

## <a name="return-value"></a>반환 값

클래스 템플릿은의 복사본을 저장 합니다 `pfunc` . 반환 하는 멤버 함수 `operator()` 를 정의 `(* pfunc)(Left, right)` 합니다.

## <a name="remarks"></a>설명

이진 함수 포인터는 함수 개체이며, 매개 변수로 이진 함수를 사용해야 하는 C++ 표준 라이브러리 알고리즘으로 전달할 수는 있지만 조정할 수는 없습니다. 부 정자와와 함께 사용 하거나 값을 사용 하는 등의 어댑터와 함께 사용 하려면 이러한 조정 작업을 가능 하 게 하는 중첩 형식, 및를 제공 해야 합니다 `first_argument_type` `second_argument_type` `result_type` . `pointer_to_binary_function`을 사용하여 변환을 수행하면 함수 어댑터를 이진 함수 포인터와 함께 사용할 수 있습니다.

## <a name="example"></a>예제

`pointer_to_binary_function`의 생성자는 직접 사용되는 경우가 거의 없습니다. `pointer_to_binary_function` 어댑터 조건자를 선언하고 사용하는 방법의 예제는 도우미 함수 [ptr_fun](../standard-library/functional-functions.md#ptr_fun)을 참조하세요.
