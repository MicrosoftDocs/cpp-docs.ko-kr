---
title: const_mem_fun_t 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::const_mem_fun_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b813128f07376d017a3ea76d6bb359db437f6f3
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100198"
---
# <a name="constmemfunt-class"></a>const_mem_fun_t 클래스

참조 인수를 사용하여 초기화할 때 인수를 사용하지 않는 const 멤버 함수를 단항 함수 개체로 호출할 수 있도록 하는 어댑터 클래스입니다.

## <a name="syntax"></a>구문

```cpp
template <class Result, class Type>
class const_mem_fun_t : public unary_function <Type *, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type* Pleft) const;
};
```

### <a name="parameters"></a>매개 변수

*Pm*<br/>
함수 개체로 변환할 `Type` 클래스의 멤버 함수 포인터입니다.

*Pleft*<br/>
개체는 합니다 *Pm* 멤버 함수가 호출 됩니다.

## <a name="return-value"></a>반환 값

조정 가능한 단항 함수입니다.

## <a name="remarks"></a>설명

복사본을 저장 하는 템플릿 클래스 *Pm*, 클래스의 멤버 함수에 대 한 포인터 여야 `Type`, 전용 멤버 개체에 있습니다. 또한 해당 멤버 함수 `operator()`가 ( `Pleft`->\* `Pm`)() **const**를 반환하는 것으로 정의합니다.

## <a name="example"></a>예제

`const_mem_fun_t`의 생성자는 일반적으로 직접 사용되지 않습니다. 도우미 함수 `mem_fun`은 멤버 함수를 적용하는 데 사용됩니다. 멤버 함수 어댑터를 사용하는 방법에 대한 예제는 [mem_fun](../standard-library/functional-functions.md#mem_fun)을 참조하세요.

## <a name="requirements"></a>요구 사항

**헤더:** \<functional>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
