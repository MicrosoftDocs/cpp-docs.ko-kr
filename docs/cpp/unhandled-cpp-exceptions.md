---
description: '자세히 알아보기: 처리 되지 않은 c + + 예외'
title: 처리되지 않은 C++ 예외
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], unhandled exceptions
- catch keyword [C++], handler not found
- exceptions [C++], unhandled
- C++ exception handling, unhandled exceptions
- unhandled exceptions [C++]
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
ms.openlocfilehash: 68bd8740d86df3faf4a83b7b2f269def5eeb5eca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145745"
---
# <a name="unhandled-c-exceptions"></a>처리되지 않은 C++ 예외

현재 예외에 대해 일치 하는 처리기 (또는 줄임표 **`catch`** 처리기)를 찾을 수 없는 경우 미리 정의 된 `terminate` 런타임 함수가 호출 됩니다. (처리기를 명시적으로 호출할 수도 있습니다 `terminate` .) 의 기본 동작은를 `terminate` 호출 하는 것입니다 `abort` . 애플리케이션을 종료하기 전에 `terminate`로 프로그램의 몇 가지 다른 함수를 호출하려면 단일 인수로 호출되는 함수 이름을 사용하여 `set_terminate` 함수를 호출합니다. `set_terminate`는 프로그램에서 언제든지 호출할 수 있습니다. `terminate`루틴은 항상에 대 한 인수로 지정 된 마지막 함수를 호출 합니다 `set_terminate` .

## <a name="example"></a>예제

다음 예제는 `char *` 예외를 throw하지만 `char *` 형식의 예외를 catch하도록 지정된 처리기를 포함하지 않습니다. `set_terminate` 호출은 `terminate`가 `term_func`를 호출하도록 명령합니다.

```cpp
// exceptions_Unhandled_Exceptions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
void term_func() {
   cout << "term_func was called by terminate." << endl;
   exit( -1 );
}
int main() {
   try
   {
      set_terminate( term_func );
      throw "Out of memory!"; // No catch handler for this exception
   }
   catch( int )
   {
      cout << "Integer exception raised." << endl;
   }
   return 0;
}
```

## <a name="output"></a>출력

```Output
term_func was called by terminate.
```

`term_func` 함수는 `exit`를 호출하여 프로그램이나 현재 스레드를 종료합니다. 이 호출이 호출자로 반환되면 `abort`가 호출됩니다.

## <a name="see-also"></a>참고 항목

[예외 및 오류 처리에 대 한 최신 c + + 모범 사례](../cpp/errors-and-exception-handling-modern-cpp.md)
