---
description: '예외: 예외에서 개체 해제에 대해 자세히 알아보세요.'
title: '예외: 예외의 개체 해제'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
ms.openlocfilehash: 47b10f3ecb96875ceee986eadda4595d2afbb77e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290559"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>예외: 예외의 개체 해제

이 문서에서는 예외 발생 시 개체를 해제 하는 데 필요한 및 방법에 대해 설명 합니다. 다룰 주제는 다음과 같습니다.

- [로컬에서 예외 처리](#_core_handling_the_exception_locally)

- [개체를 삭제 한 후 예외 throw](#_core_throwing_exceptions_after_destroying_objects)

프레임 워크 또는 응용 프로그램에서 throw 되는 예외는 일반적인 프로그램 흐름을 중단 합니다. 따라서 예외가 throw 되는 경우 개체를 적절 하 게 삭제할 수 있도록 개체를 계속 추적 하는 것이 매우 중요 합니다.

이 작업을 수행 하는 두 가지 주요 방법이 있습니다.

- 및 키워드를 사용 하 여 예외를 로컬로 처리 한 다음 문을 사용 하 여 **`try`** **`catch`** 모든 개체를 삭제 합니다.

- **`catch`** 추가 처리를 위해 블록 외부에 예외를 throw 하기 전에 블록의 모든 개체를 삭제 합니다.

이러한 두 가지 방법은 다음과 같은 문제 예에 대 한 해결 방법입니다.

[!code-cpp[NVC_MFCExceptions#14](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

위에서 작성 한 대로에서 `myPerson` 예외가 throw 되 면이 삭제 되지 않습니다 `SomeFunc` . 실행은 일반적인 함수 종료와 개체를 삭제 하는 코드를 무시 하 고 다음 외부 예외 처리기로 직접 이동 합니다. 예외가 함수를 떠날 때 개체에 대 한 포인터는 범위를 벗어납니다. 프로그램이 실행 되는 동안에는 개체가 차지 하는 메모리가 복구 되지 않습니다. 이는 메모리 누수입니다. 메모리 진단을 사용 하 여 검색할 수 있습니다.

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a> 로컬에서 예외 처리

**Try/catch** 패러다임은 메모리 누수를 방지 하 고 예외가 발생할 때 개체가 제거 되도록 하는 방어 프로그래밍 메서드를 제공 합니다. 예를 들어이 문서의 앞부분에 표시 된 예제를 다음과 같이 다시 작성할 수 있습니다.

[!code-cpp[NVC_MFCExceptions#15](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

이 새 예제에서는 예외를 catch 하 고 로컬로 처리 하는 예외 처리기를 설정 합니다. 그런 다음 함수를 정상적으로 종료 하 고 개체를 소멸 시킵니다. 이 예제의 중요 한 측면은 예외를 catch 하는 컨텍스트가 **try/catch** 블록을 사용 하 여 설정 된다는 것입니다. 로컬 예외 프레임이 없으면 함수는 예외가 throw 되었음을 알 수 없으며 정상적으로 종료 하 고 개체를 삭제할 수 없습니다.

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a> 개체를 삭제 한 후 예외 throw

예외를 처리 하는 또 다른 방법은 다음 외부 예외 처리 컨텍스트에이를 전달 하는 것입니다. 블록에서 **`catch`** 로컬에 할당 된 개체를 정리 하 고 추가 처리를 위해 예외를 throw 할 수 있습니다.

Throw 함수는 힙 개체의 할당을 취소할 수도 있고 그렇지 않을 수도 있습니다. 정상적인 경우를 반환 하기 전에 함수에서 항상 힙 개체의 할당을 취소 하는 경우 함수는 예외를 throw 하기 전에 힙 개체의 할당을 취소 해야 합니다. 반면, 함수는 일반적으로 반환 하기 전에 개체의 할당을 취소 하지 않는 경우 힙 개체의 할당을 취소 해야 하는지 여부를 사례별로 결정 해야 합니다.

다음 예제에서는 로컬로 할당 된 개체를 정리 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFCExceptions#16](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

예외 메커니즘은 프레임 개체를 자동으로 할당 취소 합니다. frame 개체의 소멸자도 호출 됩니다.

예외를 throw 할 수 있는 함수를 호출 하는 경우 **try/catch** 블록을 사용 하 여 예외를 catch 하 고 사용자가 만든 개체를 제거할 수 있는지 확인할 수 있습니다. 특히 대부분의 MFC 함수에서 예외를 throw 할 수 있습니다.

자세한 내용은 [예외: 예외 catch 및 삭제](exceptions-catching-and-deleting-exceptions.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[예외 처리](exception-handling-in-mfc.md)
