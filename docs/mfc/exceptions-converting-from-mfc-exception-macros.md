---
description: '자세한 정보: 예외: MFC 예외 매크로에서 변환'
title: '예외: MFC 예외 매크로에서 변환'
ms.date: 08/27/2018
helpviewer_keywords:
- converting exceptions [MFC]
- exception objects [MFC]
- conversions [MFC], code written with MFC macros
- keywords [MFC], macros
- macrosv, C++ keywords
- exception objects [MFC], deleting
- CException class [MFC], deleting CException class objects
- exceptions [MFC], converting
- exceptions [MFC], deleting exception objects
- catch blocks [MFC], delimiting
- exception handling [MFC], converting exceptions
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
ms.openlocfilehash: 83d4522dff902681e26a2bd098b46fea92bf1c6a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290702"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>예외: MFC 예외 매크로에서 변환

이는 고급 항목입니다.

이 문서에서는 c + + 예외 처리 키워드, 및를 사용 하기 위해 **TRY**, **CATCH**, **THROW** 등의 Microsoft Foundation Class 매크로로 작성 된 기존 코드를 변환 하는 방법을 설명 합니다 **`try`** **`catch`** **`throw`** . 다룰 주제는 다음과 같습니다.

- [변환 이점](#_core_advantages_of_converting)

- [C + + 예외를 사용 하는 예외 매크로로 코드 변환](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a> 변환의 이점

MFC 버전 3.0의 매크로 구현과 이전 버전의 구현 간의 차이점을 알고 있어야 하지만 기존 코드를 변환할 필요가 없는 경우가 있습니다. 이러한 차이점과 코드 동작의 이후 변경 사항은 [예외: 버전 3.0의 예외 매크로 변경](exceptions-changes-to-exception-macros-in-version-3-0.md)사항에 설명 되어 있습니다.

변환의 주요 이점은 다음과 같습니다.

- C + + 예외 처리 키워드를 사용 하는 코드는 약간 더 작은 값으로 컴파일됩니다. EXE 또는. GDIPLUS.DLL.

- C + + 예외 처리 키워드는 더 다양 하 게 사용할 수 있습니다. 즉,, 등을 통해 복사할 수 있는 모든 데이터 형식의 예외를 처리할 수 있는 **`int`** **`float`** **`char`** 반면 매크로는 클래스 및이 클래스에서 파생 된 클래스의 예외만 처리 `CException` 합니다.

매크로와 키워드의 주요 차이점은 "자동" 매크로를 사용 하는 코드는 예외가 범위를 벗어날 때 catch 된 예외를 삭제 하는 것입니다. 키워드를 사용 하는 코드는 그렇지 않으므로 catch 된 예외를 명시적으로 삭제 해야 합니다. 자세한 내용은 예외 [: 예외 catch 및 삭제](exceptions-catching-and-deleting-exceptions.md)문서를 참조 하세요.

또 다른 차이점은 구문입니다. 매크로와 키워드의 구문은 다음과 같은 세 가지 측면에서 다릅니다.

1. 매크로 인수 및 예외 선언:

   **CATCH** 매크로 호출의 구문은 다음과 같습니다.

   **CATCH (** *exception_class*, *exception_object_pointer_name* **)**

   클래스 이름과 개체 포인터 이름 사이의 쉼표를 확인 합니다.

   키워드에 대 한 예외 선언에서는 **`catch`** 다음 구문을 사용 합니다.

   **catch (** *exception_type* *exception_name* **)**

   이 exception 선언문은 catch 블록이 처리 하는 예외의 형식을 나타냅니다.

2. Catch 블록의 Delimitation:

   매크로를 사용 하 여 **catch** 매크로 (인수 포함)는 첫 번째 catch 블록을 시작 합니다. **AND_CATCH** 매크로는 후속 catch 블록을 시작 하 고 **END_CATCH** 매크로는 catch 블록의 시퀀스를 종료 합니다.

   키워드를 사용 하 여 **`catch`** 키워드 (예외 선언 포함)는 각 catch 블록을 시작 합니다. **END_CATCH** 매크로에 상응 하는 항목이 없습니다. catch 블록은 닫는 중괄호로 끝납니다.

3. Throw 식:

   매크로는 **THROW_LAST** 을 사용 하 여 현재 예외를 다시 THROW 합니다. **`throw`** 인수가 없는 키워드는 동일한 효과를 가집니다.

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a> 변환 수행

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>C + + 예외 처리 키워드를 사용 하기 위해 매크로를 사용 하 여 코드를 변환 하려면

1. **TRY**, **CATCH**, **AND_CATCH**, **END_CATCH**, **THROW** 및 **THROW_LAST** MFC 매크로의 모든 항목을 찾습니다.

2. 다음 매크로의 모든 항목을 바꾸거나 삭제 합니다.

   **시도** (로 바꾸기 **`try`** )

   **CATCH** (로 바꾸기 **`catch`** )

   **AND_CATCH** (으)로 바꾸기 **`catch`**

   **END_CATCH** (삭제)

   **THROW** (로 바꾸기 **`throw`** )

   **THROW_LAST** (으)로 바꾸기 **`throw`**

3. 올바른 예외 선언을 구성 하도록 매크로 인수를 수정 합니다.

   예를 들어 다음을 변경합니다.

   [!code-cpp[NVC_MFCExceptions#6](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   to

   [!code-cpp[NVC_MFCExceptions#7](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. 필요에 따라 예외 개체를 삭제 하도록 catch 블록의 코드를 수정 합니다. 자세한 내용은 예외 [: 예외 catch 및 삭제](exceptions-catching-and-deleting-exceptions.md)문서를 참조 하세요.

다음은 MFC 예외 매크로를 사용 하는 예외 처리 코드의 예제입니다. 다음 예제의 코드는 매크로를 사용 하기 때문에 예외가 `e` 자동으로 삭제 됩니다.

[!code-cpp[NVC_MFCExceptions#8](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

다음 예제의 코드는 c + + 예외 키워드를 사용 하므로 예외를 명시적으로 삭제 해야 합니다.

[!code-cpp[NVC_MFCExceptions#9](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

자세한 내용은 [예외: MFC 매크로 및 c + + 예외 사용](exceptions-using-mfc-macros-and-cpp-exceptions.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[예외 처리](exception-handling-in-mfc.md)<br/>
