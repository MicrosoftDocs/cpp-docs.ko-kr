---
description: '자세히 알아보기: setjmp 및를 사용 합니다.'
title: Setjmp 및 사용
ms.date: 08/14/2018
f1_keywords:
- longjmp_cpp
- setjmp_cpp
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
ms.openlocfilehash: 5d0f62eeed8b2401309f339a59872c7dd0ac3107
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116745"
---
# <a name="using-setjmp-and-longjmp"></a>Setjmp 및 사용

[Setjmp](../c-runtime-library/reference/setjmp.md) 및 사용 된 [jmp](../c-runtime-library/reference/longjmp.md) 를 함께 사용 하면 비로컬를 실행 하는 방법을 제공 **`goto`** 합니다. 일반적으로 표준 호출 또는 반환 규칙을 사용 하지 않고 이전에 호출 된 루틴에서 오류 처리 또는 복구 코드에 실행 제어를 전달 하기 위해 C 코드에서 사용 됩니다.

> [!CAUTION]
> `setjmp`및 `longjmp` 는 c + + 컴파일러 간에 간단 된 스택 프레임 개체의 올바른 소멸을 지원 하지 않으므로 로컬 변수에 대 한 최적화를 방지 하 여 성능을 저하 시킬 수 있기 때문에 c + + 프로그램에서 사용 하지 않는 것이 좋습니다. 대신 및 구문을 사용 하는 것이 좋습니다 **`try`** **`catch`** .

`setjmp`C + + 프로그램에서 및를 사용 하기로 결정 한 경우 `longjmp` 또는를 포함 \<setjmp.h> 하 여 \<setjmpex.h> 함수 및 SEH (구조적 예외 처리) 또는 c + + 예외 처리 간의 올바른 상호 작용을 보장 합니다.

**Microsoft 전용**

[/Eh](../build/reference/eh-exception-handling-model.md) 옵션을 사용 하 여 c + + 코드를 컴파일하는 경우 스택 해제 중에 로컬 개체에 대 한 소멸자가 호출 됩니다. 그러나 **/EHs** 또는 **/ehsc** 를 사용 하 여 컴파일하는 경우 [noexcept](../cpp/noexcept-cpp.md) 호출을 사용 하는 함수 중 하나를 사용 하면 `longjmp` 최적화 프로그램 상태에 따라 해당 함수에 대 한 소멸자 해제가 발생 하지 않을 수 있습니다.

이식 가능한 코드에서 `longjmp` 호출이 실행 될 때 프레임 기반 개체의 올바른 소멸은 표준에 의해 명시적으로 보장 되지 않으며 다른 컴파일러에서 지원 되지 않을 수 있습니다. 경고 수준 4에서를 호출 하면 `setjmp` 경고 C4611: ' _setjmp '과 c + + 개체 소멸 간의 상호 작용이 이식 가능 하지 않습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[C (구조적) 및 c + + 예외 혼합](../cpp/mixing-c-structured-and-cpp-exceptions.md)
