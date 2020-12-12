---
description: '자세한 정보: 예외 사양 (throw, noexcept) (c + +)'
title: 예외 사양 (throw, noexcept) (c + +)
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: a6b3cb808caf464dc3dd19ea4d34e9d68f09d0d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164804"
---
# <a name="exception-specifications-throw-noexcept-c"></a>예외 사양 (throw, noexcept) (c + +)

예외 사양은 함수에서 전파할 수 있는 예외 형식에 대 한 프로그래머의 의도를 나타내는 c + + 언어 기능입니다. *예외 사양을* 사용 하 여 함수가 예외를 사용 하 여 종료 될 수 있도록 지정할 수 있습니다. 컴파일러는이 정보를 사용 하 여 함수에 대 한 호출을 최적화 하 고 예기치 않은 예외가 함수를 이스케이프 하는 경우 프로그램을 종료할 수 있습니다.

C + + 17 이전에는 두 가지 종류의 예외 사양이 있었습니다. *Noexcept 사양은* c + + 11에서 새로 만들어졌습니다. 함수를 이스케이프할 수 있는 잠재적인 예외 집합이 비어 있는지 여부를 지정 합니다. *동적 예외 사양* 또는 `throw(optional_type_list)` 사양은 c + + 11에서 사용 되지 않고의 별칭인를 제외 하 고 c + + 17에서 제거 되었습니다 `throw()` `noexcept(true)` . 이 예외 사양은 함수에서 throw 할 수 있는 예외에 대 한 요약 정보를 제공 하도록 설계 되었지만 실제로는 문제가 있는 것으로 확인 되었습니다. 약간 유용한 것으로 입증 된 하나의 동적 예외 사양은 무조건 `throw()` 사양입니다. 예를 들어 함수 선언은 다음과 같습니다.

```cpp
void MyFunction(int i) throw();
```

컴파일러에 함수가 아무 예외도 throw하지 않음을 알립니다. 그러나 **/std: c + + 14** 모드에서는 함수가 예외를 throw 하는 경우 정의 되지 않은 동작이 발생할 수 있습니다. 따라서 위의 항목 대신 [noexcept](../cpp/noexcept-cpp.md) 연산자를 사용 하는 것이 좋습니다.

```cpp
void MyFunction(int i) noexcept;
```

다음 표에서는 예외 사양의 Microsoft c + + 구현을 요약 합니다.

|예외 사양|의미|
|-----------------------------|-------------|
|**`noexcept`**<br/>`noexcept(true)`<br/>`throw()`|이 함수는 예외를 throw하지 않습니다. [/Std: c + + 14](../build/reference/std-specify-language-standard-version.md) 모드 (기본값)에서는 **`noexcept`** 및 `noexcept(true)` 가 동일 합니다. 또는로 선언 된 함수에서 예외가 throw 되 면 **`noexcept`** `noexcept(true)` [std:: terminate](../standard-library/exception-functions.md#terminate) 가 호출 됩니다. `throw()` **/Std: c + + 14** 모드로 선언 된 함수에서 예외가 throw 되는 경우 결과는 정의 되지 않은 동작입니다. 특정 함수가 호출 되지 않습니다. 이는 컴파일러에서 [std::](../standard-library/exception-functions.md#unexpected)를 호출 하는 데 필요한 c + + 14 표준과의 차이입니다.  <br/> **Visual Studio 2017 버전 15.5 이상**: **/std: c + + 17** 모드에서,, **`noexcept`** `noexcept(true)` 및 `throw()` 는 모두 동일 합니다. **/Std: c + + 17** 모드에서 `throw()` 는에 대 한 별칭입니다 `noexcept(true)` . **/Std: c + + 17** 모드에서 이러한 사양 중 하나를 사용 하 여 선언 된 함수에서 예외가 throw 되는 경우 [std:: Terminate](../standard-library/exception-functions.md#terminate) 는 c + + 17 표준에 필요한 대로 호출 됩니다.|
|`noexcept(false)`<br/>`throw(...)`<br/>사양 없음|함수는 모든 형식의 예외를 throw 할 수 있습니다.|
|`throw(type)`| (**C + + 14 및 이전**) 함수는 형식의 예외를 throw 할 수 있습니다 `type` . 컴파일러는 구문을 수락 하지만로 해석 `noexcept(false)` 합니다. **/Std: c + + 17** 모드에서 컴파일러는 경고 될 때 c5043를 발생 시킵니다.|

응용 프로그램에서 예외 처리를 사용 하는 경우, 또는로 표시 된 함수의 외부 범위를 종료 하기 전에 throw 된 예외를 처리 하는 함수가 호출 스택에 있어야 합니다 **`noexcept`** `noexcept(true)` `throw()` . 예외를 throw 하는 함수 및 예외를 처리 하는 함수 사이에 호출 된 함수가 **`noexcept`** , `noexcept(true)` (또는 `throw()` **/std: c + + 17** 모드에서)로 지정 된 경우 noexcept 함수가 예외를 전파할 때 프로그램이 종료 됩니다.

함수의 예외 동작은 다음 요소에 따라 달라 집니다.

- 설정 된 [언어 표준 컴파일 모드](../build/reference/std-specify-language-standard-version.md) 입니다.
- C 또는 C++에서 함수를 컴파일하는지 여부

- 사용할 [/EH](../build/reference/eh-exception-handling-model.md) 컴파일러 옵션입니다.

- 예외 사양을 명시적으로 지정하는지 여부

C 함수에서는 명시적 예외 사양이 허용되지 않습니다. C 함수는 **/ehsc** 에서 예외를 throw 하지 않는 것으로 간주 되며, **/EHs**, **/eha** 또는 **/EHac** 에서 구조적 예외를 throw 할 수 있습니다.

다음 표에서는 다양 한 컴파일러 예외 처리 옵션에서 c + + 함수가 잠재적으로 발생할 수 있는지 여부를 요약 합니다.

|함수|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|예외 사양이 없는 C++ 함수|예|예|예|예|
|**`noexcept`**, `noexcept(true)` 또는 `throw()` 예외 사양을 사용 하는 c + + 함수|아니요|아니요|예|예|
|`noexcept(false)`, `throw(...)` 또는 `throw(type)` 예외 사양을 사용 하는 c + + 함수|예|예|예|예|

## <a name="example"></a>예제

```cpp
// exception_specification.cpp
// compile with: /EHs
#include <stdio.h>

void handler() {
   printf_s("in handler\n");
}

void f1(void) throw(int) {
   printf_s("About to throw 1\n");
   if (1)
      throw 1;
}

void f5(void) throw() {
   try {
      f1();
   }
   catch(...) {
      handler();
    }
}

// invalid, doesn't handle the int exception thrown from f1()
// void f3(void) throw() {
//   f1();
// }

void __declspec(nothrow) f2(void) {
   try {
      f1();
   }
   catch(int) {
      handler();
    }
}

// only valid if compiled without /EHc
// /EHc means assume extern "C" functions don't throw exceptions
extern "C" void f4(void);
void f4(void) {
   f1();
}

int main() {
   f2();

   try {
      f4();
   }
   catch(...) {
      printf_s("Caught exception from f4\n");
   }
   f5();
}
```

```Output
About to throw 1
in handler
About to throw 1
Caught exception from f4
About to throw 1
in handler
```

## <a name="see-also"></a>참고 항목

[try, throw 및 catch 문(C++)](../cpp/try-throw-and-catch-statements-cpp.md)<br/>
[예외 및 오류 처리에 대 한 최신 c + + 모범 사례](errors-and-exception-handling-modern-cpp.md)
