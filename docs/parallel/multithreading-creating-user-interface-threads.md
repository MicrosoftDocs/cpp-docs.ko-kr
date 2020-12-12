---
description: '자세한 정보: 다중 스레딩: MFC User-Interface 스레드 만들기'
title: '다중 스레딩: MFC User-Interface 스레드 만들기'
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
ms.openlocfilehash: bb3e388918f8881fbdd1968ef953da3067904350
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149970"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>다중 스레딩: MFC User-Interface 스레드 만들기

사용자 인터페이스 스레드는 일반적으로 사용자 입력을 처리 하 고 응용 프로그램의 다른 부분을 실행 하는 스레드와 별개로 사용자 이벤트에 응답 하는 데 사용 됩니다. 기본 응용 프로그램 스레드 ( `CWinApp` 파생 클래스에 제공 됨)가 이미 만들어져 시작 되었습니다. 이 항목에서는 추가 사용자 인터페이스 스레드를 만드는 데 필요한 단계에 대해 설명 합니다.

사용자 인터페이스 스레드를 만들 때 가장 먼저 해야 할 일은 [CWinThread](../mfc/reference/cwinthread-class.md)에서 클래스를 파생 하는 것입니다. [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) 및 [IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) 매크로를 사용 하 여이 클래스를 선언 하 고 구현 해야 합니다. 이 클래스는 일부 함수를 재정의 하 고 다른 함수를 재정의할 수 있어야 합니다. 이러한 함수와 이러한 함수는 다음 표에 나와 있습니다.

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>User-Interface 스레드를 만들 때 재정의할 함수

|함수|용도|
|--------------|-------------|
|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)|스레드가 종료 될 때 정리를 수행 합니다. 일반적으로 재정의 됩니다.|
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|스레드 인스턴스 초기화를 수행 합니다. 을 재정의 해야 합니다.|
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)|스레드별 유휴 시간 처리를 수행 합니다. 일반적으로 재정의 되지 않습니다.|
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)|메시지를 및로 디스패치하기 전에 필터링 `TranslateMessage` `DispatchMessage` 합니다. 일반적으로 재정의 되지 않습니다.|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|스레드의 메시지 및 명령 처리기가 throw 한 처리 되지 않은 예외를 가로챕니다. 일반적으로 재정의 되지 않습니다.|
|[Run](../mfc/reference/cwinthread-class.md#run)|스레드에 대 한 제어 함수입니다. 메시지 펌프를 포함 합니다. 거의 재정의 되지 않습니다.|

MFC는 매개 변수 오버로드를 통해 `AfxBeginThread`의 두 가지 버전을 제공합니다. 하나는 작업자 스레드만 만들 수 있고, 다른 하나는 사용자 인터페이스 스레드 또는 작업자 스레드를 만들 수 있습니다. 사용자 인터페이스 스레드를 시작 하려면 [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)의 두 번째 오버 로드를 호출 하 여 다음 정보를 제공 합니다.

- 에서 파생 된 클래스의 [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) 입니다 `CWinThread` .

- 필드 원하는 우선 순위 수준입니다. 기본값은 보통 우선 순위입니다. 사용 가능한 우선 순위 수준에 대 한 자세한 내용은 Windows SDK [Setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 를 참조 하십시오.

- 필드 스레드의 원하는 스택 크기입니다. 기본값은 만들기 스레드와 동일한 크기 스택입니다.

- 필드 일시 중단 된 상태에서 스레드를 만들도록 하려면 CREATE_SUSPENDED 합니다. 기본값은 0 또는 스레드를 정상적으로 시작 하는 것입니다.

- 필드 원하는 보안 특성입니다. 기본값은 부모 스레드와 동일한 액세스입니다. 이 보안 정보의 형식에 대 한 자세한 내용은 Windows SDK [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 을 참조 하세요.

`AfxBeginThread` 대부분의 작업을 수행 합니다. 클래스의 새 개체를 만들고, 사용자가 제공 하는 정보를 사용 하 여 초기화 하 고, [CWinThread:: CreateThread](../mfc/reference/cwinthread-class.md#createthread) 를 호출 하 여 스레드 실행을 시작 합니다. 모든 개체를 생성 하는 데 실패 하는 경우 모든 개체의 할당이 제대로 취소 되는지 확인 하기 위해 전체 절차를 수행 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [다중 스레딩: 스레드 종료](multithreading-terminating-threads.md)

- [다중 스레딩: 작업자 스레드 만들기](multithreading-creating-worker-threads.md)

- [프로세스 및 스레드](/windows/win32/ProcThread/processes-and-threads)

## <a name="see-also"></a>참고 항목

[C++ 및 MFC에서 다중 스레딩](multithreading-with-cpp-and-mfc.md)
