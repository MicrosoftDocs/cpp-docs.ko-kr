---
description: '자세한 정보: c + + 및 MFC를 사용 하는 다중 스레딩'
title: C++ 및 MFC에서 다중 스레딩
ms.date: 08/27/2018
helpviewer_keywords:
- MFC [C++], multithreading
- threading [C++], MFC
- worker threads [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], about threading
- CWinThread class, purpose of
- multithreading [C++], MFC
- threading [MFC]
- user interface threads [C++]
ms.assetid: 979605f8-3988-44b5-ac9c-b8cce7fcce14
ms.openlocfilehash: a553f6364f52ce8d91e08e3bb5b0e83b48575fdc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149814"
---
# <a name="multithreading-with-c-and-mfc"></a>C++ 및 MFC에서 다중 스레딩

MFC (Microsoft Foundation Class) 라이브러리는 다중 스레드 응용 프로그램에 대 한 지원을 제공 합니다. 이 항목에서는 프로세스 및 스레드와 다중 스레딩에 대 한 MFC 접근 방법에 대해 설명 합니다.

프로세스는 응용 프로그램의 실행 인스턴스입니다. 예를 들어 메모장 아이콘을 두 번 클릭 하면 메모장을 실행 하는 프로세스를 시작 합니다.

스레드는 프로세스 내의 실행 경로입니다. 메모장을 시작 하면 운영 체제에서 프로세스를 만들고 해당 프로세스의 기본 스레드 실행을 시작 합니다. 이 스레드가 종료 되 면 프로세스가 수행 됩니다. 이 주 스레드는 함수 주소 형식으로 시작 코드를 통해 운영 체제에 제공 됩니다. 일반적으로 `main` 제공 되는 또는 함수의 주소입니다 `WinMain` .

원하는 경우 응용 프로그램에서 추가 스레드를 만들 수 있습니다. 사용자가 완료 될 때까지 기다리지 않으려면 백그라운드 또는 유지 관리 작업을 처리 하기 위해이 작업을 수행 하는 것이 좋습니다. MFC 응용 프로그램의 모든 스레드는 [CWinThread](../mfc/reference/cwinthread-class.md) 개체로 표시 됩니다. 대부분의 경우에는 이러한 개체를 명시적으로 만들 필요가 없습니다. 대신 프레임 워크 도우미 함수 [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)를 호출 하 여 개체를 만듭니다 `CWinThread` .

MFC는 사용자 인터페이스 스레드와 작업자 스레드 라는 두 가지 유형의 스레드를 구분 합니다. 사용자 인터페이스 스레드는 일반적으로 사용자 입력을 처리 하 고 사용자가 생성 한 이벤트와 메시지에 응답 하는 데 사용 됩니다. 작업자 스레드는 일반적으로 사용자 입력이 필요 하지 않은 다시 계산 등의 작업을 완료 하는 데 사용 됩니다. Win32 API는 스레드 유형을 구분 하지 않습니다. 스레드 실행을 시작할 수 있도록 스레드의 시작 주소를 알고 있어야 합니다. MFC는 사용자 인터페이스에서 이벤트에 대 한 메시지 펌프를 제공 하 여 사용자 인터페이스 스레드를 특별히 처리 합니다. `CWinApp` 는에서 파생 되 `CWinThread` 고 사용자가 생성 한 이벤트와 메시지를 처리 하기 때문에 사용자 인터페이스 스레드 개체의 한 예입니다.

두 개 이상의 스레드가 동일한 개체에 액세스 해야 하는 경우에 특히 주의 해야 합니다. [다중 스레딩: 프로그래밍 팁](multithreading-programming-tips.md) 에서는 이러한 상황에서 발생할 수 있는 문제를 해결 하는 데 사용할 수 있는 기술을 설명 합니다. [다중 스레딩: 동기화 클래스를 사용 하는 방법](multithreading-how-to-use-the-synchronization-classes.md) 에서는 여러 스레드의 액세스를 단일 개체로 동기화 하는 데 사용할 수 있는 클래스를 사용 하는 방법을 설명 합니다.

한 번에 둘 이상의 스레드에서 개체에 액세스 하지 않도록 해야 하므로 다중 스레드 프로그래밍 작성 및 디버깅은 본질적으로 복잡 하 고 까다로운 일입니다. 다중 스레딩 항목에서는 다중 스레드 프로그램의 기본 사항에 대해 설명 하지 않으며 다중 스레드 프로그램에서 MFC를 사용 하는 방법에 대해서만 설명 합니다. Visual C++에 포함 된 다중 스레드 MFC 샘플에서는 MFC에 포함 되지 않은 몇 가지 다중 스레드 추가 기능 및 Win32 Api를 보여 줍니다. 그러나 시작 지점 으로만 사용 됩니다.

운영 체제에서 프로세스 및 스레드를 처리 하는 방법에 대 한 자세한 내용은 Windows SDK의 [프로세스 및 스레드](/windows/win32/ProcThread/processes-and-threads) 를 참조 하세요.

MFC 다중 스레딩 지원에 대 한 자세한 내용은 다음 항목을 참조 하십시오.

- [다중 스레딩: User-Interface 스레드 만들기](multithreading-creating-user-interface-threads.md)

- [다중 스레딩: 작업자 스레드 만들기](multithreading-creating-worker-threads.md)

- [다중 스레딩: 동기화 클래스 사용 방법](multithreading-how-to-use-the-synchronization-classes.md)

- [다중 스레딩: 스레드 종료](multithreading-terminating-threads.md)

- [다중 스레딩: 프로그래밍 팁](multithreading-programming-tips.md)

- [다중 스레딩: 동기화 클래스를 사용 하는 경우](multithreading-when-to-use-the-synchronization-classes.md)

## <a name="see-also"></a>참고 항목

[이전 코드에 대 한 다중 스레딩 지원 (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)
