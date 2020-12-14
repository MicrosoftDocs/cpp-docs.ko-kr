---
description: '자세히 알아보기: Catch 블록을 평가 하는 방법 (c + +)'
title: Catch 블록 평가 방법 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
ms.openlocfilehash: ec4544bb88eea0ee03b7b5b0ab139e267da0552d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221295"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Catch 블록 평가 방법 (C++)

일반적으로 std::exception에서 파생되는 형식을 throw할 것을 권장하지만 C++를 사용하면 모든 형식의 예외를 throw할 수 있습니다. C + + 예외는 **`catch`** throw 된 예외와 동일한 형식을 지정 하는 처리기 또는 모든 형식의 예외를 catch 할 수 있는 처리기에 의해 catch 될 수 있습니다.

throw된 예외의 형식이 하나의 기본 클래스 또는 여러 개의 클래스를 가진 클래스인 경우 예외 형식의 기본 클래스 및 예외 형식의 기본에 대한 참조를 허용하는 처리기로 catch할 수 있습니다. 예외가 참조에 의해 catch될 때 실제 throw된 예외 개체에 바인딩됩니다. 바인딩되지 않는 예외는 복사본입니다(함수에 대한 인수와 동일).

예외가 throw 되 면 다음 형식의 처리기에 의해 catch 될 수 있습니다 **`catch`** .

- 줄임표 구문을 사용하여 모든 형식을 받아들일 수 있는 처리기.

- 예외 개체와 동일한 형식을 허용 하는 처리기입니다. 이는 복사본이 **`const`** 며 **`volatile`** 한정자는 무시 됩니다.

- 예외 개체와 동일한 형식에 대한 참조를 허용하는 처리기.

- **`const`** **`volatile`** 예외 개체와 동일한 형식의 또는 형식에 대 한 참조를 허용 하는 처리기입니다.

- 예외 개체와 동일한 형식의 기본 클래스를 허용 하는 처리기입니다. 이는 복사본 이므로 **`const`** 및 **`volatile`** 한정자는 무시 됩니다. **`catch`** 기본 클래스에 대 한 처리기는 **`catch`** 파생 클래스에 대 한 처리기 앞에 오지 않아야 합니다.

- 예외 개체와 동일한 형식의 기본 클래스에 대한 참조를 허용하는 처리기.

- **`const`** **`volatile`** 예외 개체와 동일한 형식의 기본 클래스 또는 형식에 대 한 참조를 허용 하는 처리기입니다.

- throw된 포인터 개체가 표준 포인터 변환 규칙을 통해 변환될 수 있는 대상 포인터를 허용하는 처리기.

**`catch`** 지정 된 블록에 대 한 처리기가 모양 순서 대로 검사 되기 때문에 처리기가 표시 되는 순서는 중요 합니다 **`try`** . 예를 들어 파생 클래스의 처리기 앞에 기본 클래스의 처리기를 배치하면 오류가 발생합니다. 일치 처리기를 찾은 후에는 **`catch`** 후속 처리기가 검사 되지 않습니다. 결과적으로, 줄임표 처리기는 **`catch`** 해당 블록의 마지막 처리기 여야 합니다 **`try`** . 예를 들어:

```cpp
// ...
try
{
    // ...
}
catch( ... )
{
    // Handle exception here.
}
// Error: the next two handlers are never examined.
catch( const char * str )
{
    cout << "Caught exception: " << str << endl;
}
catch( CExcptClass E )
{
    // Handle CExcptClass exception here.
}
```

이 예제에서 줄임표 처리기는 **`catch`** 검사 되는 유일한 처리기입니다.

## <a name="see-also"></a>참고 항목

[예외 및 오류 처리에 대 한 최신 c + + 모범 사례](../cpp/errors-and-exception-handling-modern-cpp.md)
