---
description: Pointer_to_unary_function 클래스에 대해 자세히 알아보세요.
title: pointer_to_unary_function 클래스
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: 45a927add90915bcbd8791eeba5561027b7e9217
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340699"
---
# <a name="pointer_to_unary_function-class"></a>pointer_to_unary_function 클래스

단항 함수 포인터를 조정 가능한 단항 함수로 변환합니다. C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다.

## <a name="syntax"></a>구문

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>매개 변수

*pfunc*\
변환할 이진 함수입니다.

*비어*\
*\* Pfunc* 가 호출 되는 개체입니다.

## <a name="return-value"></a>반환 값

클래스 템플릿은의 복사본을 저장 합니다 `pfunc` . 그리고 해당 구성원 함수 `operator()`가 (\* **pfunc**)(_ *Left*)를 반환하는 것으로 정의합니다.

## <a name="remarks"></a>설명

단항 함수 포인터는 함수 개체이며, 매개 변수로 단항 함수를 사용해야 하는 C++ 표준 라이브러리 알고리즘으로 전달할 수는 있지만 조정할 수는 없습니다. 값을 바인딩 또는 부 정자와와 함께 사용 하는 것과 같이 어댑터와 함께 사용 하려면 중첩 형식과 함께 제공 되어야 하며, 이러한 조정 작업을 `argument_type` `result_type` 가능 하 게 합니다. `pointer_to_unary_function`을 사용하여 변환을 수행하면 함수 어댑터를 이진 함수 포인터와 함께 사용할 수 있습니다.

## <a name="example"></a>예제

`pointer_to_unary_function`의 생성자는 직접 사용되는 경우가 거의 없습니다. `pointer_to_unary_function` 어댑터 조건자를 선언하고 사용하는 방법의 예제는 도우미 함수 [ptr_fun](../standard-library/functional-functions.md#ptr_fun)을 참조하세요.
