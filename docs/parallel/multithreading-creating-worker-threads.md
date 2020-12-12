---
description: '자세한 정보: 다중 스레딩: MFC에서 작업자 스레드 만들기'
title: '다중 스레딩: MFC에서 작업자 스레드 만들기'
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
ms.openlocfilehash: 75fa3122518f6fc342fe53a3df9fb9e5a78e2483
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149957"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>다중 스레딩: MFC에서 작업자 스레드 만들기

작업자 스레드는 일반적으로 사용자가 응용 프로그램을 계속 사용 하기 위해 기다릴 필요가 없는 백그라운드 작업을 처리 하는 데 사용 됩니다. 다시 계산 및 백그라운드 인쇄 등의 작업은 작업자 스레드의 좋은 예입니다. 이 항목에서는 작업자 스레드를 만드는 데 필요한 단계에 대해 자세히 설명 합니다. 다룰 주제는 다음과 같습니다.

- [스레드 시작](#_core_starting_the_thread)

- [제어 함수 구현](#_core_implementing_the_controlling_function)

- [예제](#_core_controlling_function_example)

작업자 스레드를 만드는 작업은 비교적 단순 합니다. 스레드를 실행 하는 데는 제어 함수를 구현 하 고 스레드를 시작 하는 두 단계만 필요 합니다. [CWinThread](../mfc/reference/cwinthread-class.md)에서 클래스를 파생할 필요는 없습니다. 의 특수 버전이 필요 `CWinThread` 하지만 대부분의 간단한 작업자 스레드에는 필요 하지 않은 경우 클래스를 파생 시킬 수 있습니다. 를 `CWinThread` 수정 하지 않고 사용할 수 있습니다.

## <a name="starting-the-thread"></a><a name="_core_starting_the_thread"></a> 스레드 시작

의 두 가지 오버 로드 된 버전이 있습니다 `AfxBeginThread` . 하나는 작업자 스레드만 만들 수 있고 다른 하나는 사용자 인터페이스 스레드와 작업자 스레드를 모두 만들 수 있습니다. 첫 번째 오버 로드를 사용 하 여 작업자 스레드의 실행을 시작 하려면 [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)를 호출 하 여 다음 정보를 제공 합니다.

- 제어 함수의 주소입니다.

- 제어 함수에 전달할 매개 변수입니다.

- 필드 스레드의 원하는 우선 순위입니다. 기본값은 보통 우선 순위입니다. 사용 가능한 우선 순위 수준에 대 한 자세한 내용은 Windows SDK [Setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 를 참조 하십시오.

- 필드 스레드의 원하는 스택 크기입니다. 기본값은 만들기 스레드와 동일한 크기 스택입니다.

- 필드 일시 중단 된 상태에서 스레드를 만들도록 하려면 CREATE_SUSPENDED 합니다. 기본값은 0 또는 스레드를 정상적으로 시작 하는 것입니다.

- 필드 원하는 보안 특성입니다. 기본값은 부모 스레드와 동일한 액세스입니다. 이 보안 정보의 형식에 대 한 자세한 내용은 Windows SDK [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 을 참조 하세요.

`AfxBeginThread` 개체를 만들고 초기화 하며, `CWinThread` 시작 하 고, 나중에 참조할 수 있도록 해당 주소를 반환 합니다. 모든 개체를 생성 하는 데 실패 하는 경우 모든 개체의 할당이 제대로 취소 되는지 확인 하기 위해 전체 절차를 수행 합니다.

## <a name="implementing-the-controlling-function"></a><a name="_core_implementing_the_controlling_function"></a> 제어 함수 구현

제어 함수는 스레드를 정의 합니다. 이 함수를 입력 하면 스레드가 시작 되 고 종료 될 때 스레드가 종료 됩니다. 이 함수에는 다음과 같은 프로토타입이 있어야 합니다.

```cpp
UINT MyControllingFunction( LPVOID pParam );
```

매개 변수는 단일 값입니다. 이 매개 변수에서 수신 하는 함수는 스레드 개체를 만들 때 생성자에 전달 된 값입니다. 제어 함수는 선택 하는 방식으로이 값을 해석할 수 있습니다. 스칼라 값 또는 여러 매개 변수를 포함 하는 구조체에 대 한 포인터로 처리 하거나 무시할 수 있습니다. 매개 변수가 구조체를 참조 하는 경우에는이 구조체를 사용 하 여 호출자에서 스레드로 데이터를 전달할 뿐만 아니라 스레드에서 호출자로 데이터를 다시 전달할 수도 있습니다. 이러한 구조체를 사용 하 여 데이터를 호출자에 게 다시 전달 하는 경우 스레드가 준비 되 면 호출자에 게이를 알려야 합니다. 작업자 스레드에서 호출자로 통신 하는 방법에 대 한 자세한 내용은 [다중 스레딩: 프로그래밍 팁](multithreading-programming-tips.md)을 참조 하세요.

함수가 종료 되 면 종료 이유를 나타내는 UINT 값을 반환 해야 합니다. 일반적으로이 종료 코드는 0입니다 .이 값은 다른 오류 유형을 나타내는 다른 값의 성공을 나타냅니다. 이는 전적으로 구현에 따라 달라 집니다. 일부 스레드는 개체의 사용 횟수를 유지 관리 하 고 해당 개체의 현재 사용 수를 반환할 수 있습니다. 응용 프로그램에서이 값을 검색할 수 있는 방법을 보려면 [다중 스레딩: 스레드 종료](multithreading-terminating-threads.md)를 참조 하세요.

MFC 라이브러리로 작성 된 다중 스레드 프로그램에서 수행할 수 있는 작업에는 몇 가지 제한 사항이 있습니다. 이러한 제한 사항 및 스레드 사용에 대 한 기타 팁에 대 한 설명은 [다중 스레딩: 프로그래밍 팁](multithreading-programming-tips.md)을 참조 하세요.

## <a name="controlling-function-example"></a><a name="_core_controlling_function_example"></a> 제어 함수 예제

다음 예제에서는 제어 함수를 정의 하 고 프로그램의 다른 부분에서 사용 하는 방법을 보여 줍니다.

```cpp
UINT MyThreadProc( LPVOID pParam )
{
    CMyObject* pObject = (CMyObject*)pParam;

    if (pObject == NULL ||
        !pObject->IsKindOf(RUNTIME_CLASS(CMyObject)))
    return 1;   // if pObject is not valid

    // do something with 'pObject'

    return 0;   // thread completed successfully
}

// inside a different function in the program
.
.
.
pNewObject = new CMyObject;
AfxBeginThread(MyThreadProc, pNewObject);
.
.
.
```

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [다중 스레딩: User-Interface 스레드 만들기](multithreading-creating-user-interface-threads.md)

## <a name="see-also"></a>참고 항목

[C++ 및 MFC에서 다중 스레딩](multithreading-with-cpp-and-mfc.md)
