---
description: Const_mem_fun1_ref_t 클래스에 대해 자세히 알아보세요.
title: const_mem_fun1_ref_t 클래스
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: f2d8b96c3888e3b7b07b5cccef8ce58cdedb6732
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324947"
---
# <a name="const_mem_fun1_ref_t-class"></a>const_mem_fun1_ref_t 클래스

**`const`** 참조 인수를 사용 하 여 초기화할 때 단일 인수를 사용 하는 멤버 함수를 이항 함수 개체로 호출할 수 있도록 하는 어댑터 클래스입니다. C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다.

## <a name="syntax"></a>구문

```cpp
template <class Result, class Type, class Arg>
    class const_mem_fun1_ref_t
        : public binary_function<Type, Arg, Result>
{
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
};
```

### <a name="parameters"></a>매개 변수

*M*\
함수 개체로 변환할 `Type` 클래스의 멤버 함수 포인터입니다.

*비어*\
**`const`** *Pm* 멤버 함수가 호출 되는 개체입니다.

*오른쪽*\
*Pm* 으로 지정 되는 인수입니다.

## <a name="return-value"></a>반환 값

조정 가능한 이항 함수입니다.

## <a name="remarks"></a>설명

클래스 템플릿은  `Type` 전용 멤버 개체에서 클래스의 멤버 함수에 대 한 포인터 여야 하는 Pm의 복사본을 저장 합니다. 해당 멤버 함수를 `operator()` ( `left` \* *Pm*) ()을 반환 하는 것으로 정의 `right` **`const`** 합니다.

## <a name="example"></a>예제

`const_mem_fun1_ref_t`의 생성자는 일반적으로 직접 사용되지 않습니다. 도우미 함수 `mem_fun_ref`은 멤버 함수를 적용하는 데 사용됩니다. 멤버 함수 어댑터를 사용하는 방법의 예제에 대해서는 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)를 참조하세요.
