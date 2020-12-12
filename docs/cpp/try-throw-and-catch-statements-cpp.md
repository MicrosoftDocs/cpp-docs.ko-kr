---
description: Try, throw 및 catch 문 (c + +)에 대해 자세히 알아보세요.
title: Try, Throw 및 Catch 문(C++)
ms.date: 11/04/2016
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
helpviewer_keywords:
- catch keyword [C++]
- keywords [C++], exception handling
- C++ exception handling, statement syntax
- try-catch keyword [C++], about try-catch exception handling
- throw keyword [C++]
- try-catch keyword [C++]
- try-catch keyword [C++], exception handling
- throwing exceptions [C++], throw keyword
- try-catch keyword [C++], throw keyword [C++]s
- throwing exceptions [C++], implementing C++ exception handling
- throwing exceptions [C++]
- throw keyword [C++], throw() vs. throw(...)
ms.assetid: 15e6a87b-b8a5-4032-a7ef-946c644ba12a
ms.openlocfilehash: 78dc76a9db5a4b1b6b8c23d1807b683d0dbae969
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186430"
---
# <a name="try-throw-and-catch-statements-c"></a>Try, Throw 및 Catch 문(C++)

C + +에서 예외 처리를 구현 하려면 **`try`** , **`throw`** 및 **`catch`** 식을 사용 합니다.

먼저 블록을 사용 **`try`** 하 여 예외를 throw 할 수 있는 하나 이상의 문을 묶습니다.

**`throw`** 식은 예외 조건 (종종 오류)을 블록에서 발생 했다는 신호를 보냅니다 **`try`** . 모든 형식의 개체를 식의 피연산자로 사용할 수 있습니다 **`throw`** . 일반적으로 이 개체는 일반적으로 오류 정보를 전달하는 데 사용됩니다. 대부분의 경우 [std:: exception](../standard-library/exception-class.md) 클래스 또는 표준 라이브러리에 정의 된 파생 클래스 중 하나를 사용 하는 것이 좋습니다. 그 중 하나가 적합하지 않은 경우 `std::exception`에서 사용자 고유의 예외를 파생하는 것이 좋습니다.

Throw 될 수 있는 예외를 처리 하려면 **`catch`** 블록 바로 다음에 하나 이상의 블록을 구현 **`try`** 합니다. 각 **`catch`** 블록은 처리할 수 있는 예외 형식을 지정 합니다.

이 예제에서는 **`try`** 블록 및 해당 처리기를 보여 줍니다. `GetNetworkResource()`가 네트워크 연결을 통해 데이터를 받고 두 개의 예외 형식은 `std::exception`에서 파생된 사용자 정의 클래스라고 가정합니다. 예외는 문에서 참조로 catch 됩니다 **`const`** **`catch`** . 값으로 예외를 throw하고 상수 참조로 catch하는 것이 좋습니다.

## <a name="example"></a>예제

```cpp
MyData md;
try {
   // Code that could throw an exception
   md = GetNetworkResource();
}
catch (const networkIOException& e) {
   // Code that executes when an exception of type
   // networkIOException is thrown in the try block
   // ...
   // Log error message in the exception object
   cerr << e.what();
}
catch (const myDataFormatException& e) {
   // Code that handles another exception type
   // ...
   cerr << e.what();
}

// The following syntax shows a throw expression
MyData GetNetworkResource()
{
   // ...
   if (IOSuccess == false)
      throw networkIOException("Unable to connect");
   // ...
   if (readError)
      throw myDataFormatException("Format error");
   // ...
}
```

## <a name="remarks"></a>설명

절 뒤의 코드는 **`try`** 보호 된 코드 섹션입니다. **`throw`** 식은 예외 를 발생 시킵니다. 절 뒤에 오는 코드 블록은 **`catch`** 예외 처리기입니다. 및 식의 형식이  **`throw`** **`catch`** 호환 되는 경우 throw 되는 예외를 catch 하는 처리기입니다. 블록에서 형식 일치를 제어 하는 규칙 목록은 **`catch`** [Catch 블록을 평가 하는 방법](../cpp/how-catch-blocks-are-evaluated-cpp.md)을 참조 하세요. **`catch`** 문이 형식 대신 줄임표 (...)를 지정 하는 경우 **`catch`** 블록은 모든 형식의 예외를 처리 합니다. [/Eha](../build/reference/eh-exception-handling-model.md) 옵션을 사용 하 여 컴파일하면 C 구조적 예외 및 시스템 생성 또는 응용 프로그램에서 생성 된 비동기 예외 (예: 메모리 보호, 0으로 나누기 및 부동 소수점 위반)가 포함 될 수 있습니다. **`catch`** 블록은 일치 하는 형식을 찾기 위해 프로그램 순서로 처리 되기 때문에 줄임표 처리기는 연결 된 블록의 마지막 처리기 여야 합니다 **`try`** . `catch(...)`를 주의해서 사용하십시오. catch 블록이 catch되는 특정 예외를 처리하는 방법을 알고 있는 경우가 아니면 프로그램을 계속 실행하지 마십시오. 일반적으로 `catch(...)` 블록은 오류를 기록하고 프로그램 실행을 중지하기 전에 특별한 정리 작업을 수행하는 데 사용합니다.

**`throw`** 피연산자가 없는 식은 현재 처리 되 고 있는 예외를 다시 throw 합니다. 예외를 다시 throw할 때 원래 예외의 다형 형식 정보를 보존하므로 이 폼을 사용하는 것이 좋습니다. 이러한 식은 처리기 **`catch`** 또는 처리기에서 호출 되는 함수 에서만 사용 해야 합니다 **`catch`** . 다시 throw된 예외 개체는 복사본이 아닌 원본 예외 개체입니다.

```cpp
try {
   throw CSomeOtherException();
}
catch(...) {
   // Catch all exceptions - dangerous!!!
   // Respond (perhaps only partially) to the exception, then
   // re-throw to pass the exception to some other handler
   // ...
   throw;
}
```

## <a name="see-also"></a>참고 항목

[예외 및 오류 처리에 대 한 최신 c + + 모범 사례](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[처리 되지 않은 c + + 예외](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)
