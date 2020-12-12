---
description: '자세한 정보: 이전 코드에 대 한 다중 스레딩 지원 (Visual C++)'
title: 이전 코드를 위한 다중 스레드 지원(Visual C++)
ms.date: 08/27/2018
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
ms.openlocfilehash: a3b04fdde01e2576d37d41f2860526fcf5ba1691
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149905"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>이전 코드를 위한 다중 스레드 지원(Visual C++)

Visual C++를 사용 하면 동시에 실행 되는 여러 스레드를 동시에 실행할 수 있습니다. 다중 스레딩을 사용 하면 백그라운드 작업을 끄고, 동시 입력 스트림을 관리 하 고, 사용자 인터페이스를 관리 하는 등의 작업을 수행할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용

[C 및 Wind32를 사용한 다중 스레딩](multithreading-with-c-and-win32.md)<br/>
Microsoft Windows를 사용 하 여 다중 스레드 응용 프로그램을 만들기 위한 지원을 제공 합니다.

[C++ 및 MFC에서 다중 스레딩](multithreading-with-cpp-and-mfc.md)<br/>
프로세스 및 스레드와 다중 스레딩에 대 한 MFC 접근 방법에 대해 설명 합니다.

[다중 스레딩 및 로캘](multithreading-and-locales.md)<br/>
다중 스레드 응용 프로그램에서 C 런타임 라이브러리와 c + + 표준 라이브러리의 로캘 기능을 사용할 때 발생 하는 문제에 대해 설명 합니다.

## <a name="related-sections"></a>관련 단원

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
애플리케이션 내의 실행 스레드를 나타냅니다.

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
Win32의 동기화 개체에 공통적인 기능을 제공 하는 순수 가상 클래스에 대해 설명 합니다.

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
하나 이상의 프로세스에서 제한 된 수의 스레드를 사용 하 여 리소스에 액세스할 수 있도록 하는 동기화 개체인 세마포를 나타냅니다.

[CMutex](../mfc/reference/cmutex-class.md)<br/>
한 스레드가 한 리소스에 상호 배타적으로 액세스하도록 허용하는 동기화 개체인 뮤텍스를 나타냅니다.

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
한 번에 한 스레드만 리소스 또는 코드 섹션에 액세스할 수 있도록 하는 동기화 개체인 임계 영역을 나타냅니다.

[CEvent](../mfc/reference/cevent-class.md)<br/>
한 스레드에서 이벤트가 발생 했음을 다른 스레드에 알릴 수 있도록 하는 동기화 개체인 이벤트를 나타냅니다.

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
다중 스레드 프로그램에 대한 액세스를 제어할 때 사용하는 액세스 제어 메커니즘을 나타냅니다.

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
다중 스레드 프로그램에서 한 리소스에 대한 액세스를 제어할 때 사용하는 액세스 제어 메커니즘을 나타냅니다.
