---
description: '예외: 예외 Catch 및 삭제에 대 한 자세한 정보'
title: '예외: 예외 Catch 및 삭제'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 01f018694d211b4b60acc92c4121614d14769d6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290741"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>예외: 예외 Catch 및 삭제

다음 지침 및 예제에서는 예외를 catch 하 고 삭제 하는 방법을 보여 줍니다. , 및 키워드에 대 한 자세한 내용은 **`try`** **`catch`** **`throw`** [최신 c + + 모범 사례 예외 및 오류 처리](../cpp/errors-and-exception-handling-modern-cpp.md)를 참조 하세요.

예외를 삭제 하지 못하면 코드가 예외를 catch 할 때마다 예외 처리기가 처리 하는 예외 개체를 삭제 해야 합니다.

**`catch`** 블록은 다음과 같은 경우 예외를 삭제 해야 합니다.

- **`catch`** 블록은 새 예외를 throw 합니다.

   물론 동일한 예외를 다시 throw 하는 경우 예외를 삭제 하면 안 됩니다.

   [!code-cpp[NVC_MFCExceptions#3](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- 실행은 블록 내에서 반환 **`catch`** 됩니다.

> [!NOTE]
> 를 삭제할 때 `CException` `Delete` 멤버 함수를 사용 하 여 예외를 삭제 합니다. **`delete`** 예외가 힙에 없는 경우 실패할 수 있으므로 키워드를 사용 하지 마세요.

#### <a name="to-catch-and-delete-exceptions"></a>예외를 catch 하 고 삭제 하려면

1. 키워드를 사용 **`try`** 하 여 블록을 설정 **`try`** 합니다. 블록 내에서 예외를 throw 할 수 있는 모든 프로그램 문을 실행 **`try`** 합니다.

   키워드를 사용 **`catch`** 하 여 블록을 설정 **`catch`** 합니다. 블록에 예외 처리 코드를 추가 **`catch`** 합니다. 블록 **`catch`** 내의 코드는 **`try`** 문에 지정 된 형식의 예외를 throw 하는 경우에만 블록의 코드가 실행 됩니다 **`catch`** .

   다음은 **`try`** 및 **`catch`** 블록이 일반적으로 정렬 되는 방법을 보여 줍니다.

   [!code-cpp[NVC_MFCExceptions#4](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   예외가 throw 되 면 예외 **`catch`** 선언이 예외 형식과 일치 하는 첫 번째 블록으로 제어가 전달 됩니다. 아래 나열 된 대로 순차 블록을 사용 하 여 다양 한 유형의 예외를 선택적으로 처리할 수 있습니다 **`catch`** .

   [!code-cpp[NVC_MFCExceptions#5](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

자세한 내용은 [예외: MFC 예외 매크로에서 변환](exceptions-converting-from-mfc-exception-macros.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[예외 처리](exception-handling-in-mfc.md)
