---
description: 구조화 된 예외 필터를 작성 하는 방법에 대해 자세히 알아보세요.
title: 예외 필터 작성
ms.date: 12/16/2020
helpviewer_keywords:
- exception handling [C++], filters
ms.openlocfilehash: 8b6706c7dfe0e96e26f77f1f3a452db638141803
ms.sourcegitcommit: 387ce22a3b0137f99cbb856a772b5a910c9eba99
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97645061"
---
# <a name="writing-an-exception-filter"></a>예외 필터 작성

예외 처리기의 수준으로 이동하거나 계속 실행하여 예외를 처리할 수 있습니다. 예외 처리기 코드를 사용 하 여 예외를 처리 하 고이를 사용 하는 대신 *필터* 식을 사용 하 여 문제를 정리할 수 있습니다. 그런 다음 `EXCEPTION_CONTINUE_EXECUTION` (-1)을 반환 하 여 스택을 지우지 않고 일반 흐름을 다시 시작할 수 있습니다.

> [!NOTE]
> 일부 예외는 계속할 수 없습니다. 이러한 예외에 대해 *필터가* -1로 계산 되 면 시스템은 새 예외를 발생 시킵니다. 를 호출 하 [`RaiseException`](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) 는 경우 예외를 계속할지 여부를 결정 합니다.

예를 들어 다음 코드는 *필터* 식에서 함수 호출을 사용 합니다 .이 함수는 문제를 처리 한 다음-1을 반환 하 여 정상적인 제어 흐름을 다시 시작 합니다.

```cpp
// exceptions_Writing_an_Exception_Filter.cpp
#include <windows.h>
int main() {
   int Eval_Exception( int );

   __try {}

   __except ( Eval_Exception( GetExceptionCode( ))) {
      ;
   }

}
void ResetVars( int ) {}
int Eval_Exception ( int n_except ) {
   if ( n_except != STATUS_INTEGER_OVERFLOW &&
      n_except != STATUS_FLOAT_OVERFLOW )   // Pass on most exceptions
   return EXCEPTION_CONTINUE_SEARCH;

   // Execute some code to clean up problem
   ResetVars( 0 );   // initializes data to 0
   return EXCEPTION_CONTINUE_EXECUTION;
}
```

*필터가* 복잡 한 작업을 수행 해야 할 때마다 *필터* 식에서 함수 호출을 사용 하는 것이 좋습니다. 식을 계산하면 함수가 실행됩니다. 이 경우에는 `Eval_Exception`입니다.

을 사용 하 여 [`GetExceptionCode`](/windows/win32/Debug/getexceptioncode) 예외를 확인 합니다. 이 함수는 문의 필터 식 내에서 호출 해야 합니다 **`__except`** . `Eval_Exception` 는를 호출할 수 `GetExceptionCode` 없지만 예외 코드가 전달 되어야 합니다.

이 처리기는 예외가 정수 또는 부동 소수점 오버플로가 아닌 경우 제어를 다른 처리기에 전달합니다. 그럴 경우 처리기는 함수(`ResetVars`가 유일한 예이며, API 함수가 아님)를 호출하여 일부 전역 변수를 다시 설정합니다. **`__except`** 이 예제에서 빈 문 블록은 `Eval_Exception` (1)를 반환 하지 않기 때문에 실행할 수 없습니다 `EXCEPTION_EXECUTE_HANDLER` .

함수 호출 사용은 복잡한 필터 식을 처리하는 좋은 일반 용도의 기술입니다. 유용한 두 개의 다른 C 언어 기능은 다음과 같습니다.

- 조건 연산자

- 쉼표 연산자

조건 연산자는 여기에서 자주 유용 합니다. 특정 반환 코드를 확인 한 다음 두 가지 다른 값 중 하나를 반환 하는 데 사용할 수 있습니다. 예를 들어 다음 코드의 필터는 예외가 인 경우에만 예외를 인식 합니다 `STATUS_INTEGER_OVERFLOW` .

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

다음 코드는 동일한 결과를 생성하므로 이 경우 조건 연산자의 목적은 선명도를 제공하는 것입니다.

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

조건 연산자는 필터를-1,로 평가 하려는 경우에 더 유용 합니다 `EXCEPTION_CONTINUE_EXECUTION` .

쉼표 연산자를 사용 하면 여러 개의 식을 순서 대로 실행할 수 있습니다. 그런 다음 마지막 식의 값을 반환 합니다. 예를 들어 다음 코드는 예외 코드를 변수에 저장한 다음 테스트합니다.

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>참고 항목

[예외 처리기 작성](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
