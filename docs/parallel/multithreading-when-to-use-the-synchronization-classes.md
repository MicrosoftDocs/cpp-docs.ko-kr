---
description: '자세한 정보: 다중 스레딩: MFC 동기화 클래스를 사용 하는 경우'
title: '다중 스레딩: MFC 동기화 클래스를 사용 하는 경우'
ms.date: 08/27/2018
helpviewer_keywords:
- threading [MFC], synchronization classes
- resources [C++], multithreading
- synchronization classes [C++]
- synchronization [C++], multithreading
- controlled resource access [C++]
- synchronization access classes [C++]
- threading [C++], synchronization
- multithreading [C++], synchronization classes
ms.assetid: 4914f54e-68ac-438f-93c9-c013455a657e
ms.openlocfilehash: 02776bc61ed702ee81ce0f7373dd442a9fc3d446
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149853"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>다중 스레딩: MFC 동기화 클래스를 사용 하는 경우

MFC와 함께 제공 되는 다중 스레드 클래스는 동기화 개체 ([CSyncObject](../mfc/reference/csyncobject-class.md), [CSemaphore](../mfc/reference/csemaphore-class.md), [Cmutex](../mfc/reference/cmutex-class.md), [CCriticalSection](../mfc/reference/ccriticalsection-class.md)및 [CEvent](../mfc/reference/cevent-class.md))와 동기화 액세스 개체 ([CMultiLock](../mfc/reference/cmultilock-class.md) 및 [csinglelock](../mfc/reference/csinglelock-class.md))의 두 가지 범주로 나뉩니다.

리소스의 무결성을 보장 하려면 리소스에 대 한 액세스를 제어 해야 하는 경우 동기화 클래스를 사용 합니다. 동기화 액세스 클래스는 이러한 제어 되는 리소스에 대 한 액세스 권한을 얻는 데 사용 됩니다. 이 항목에서는 각 클래스를 사용 하는 경우에 대해 설명 합니다.

사용 해야 하는 동기화 클래스를 확인 하려면 다음과 같은 일련의 질문을 확인 합니다.

1. 응용 프로그램에서 리소스에 액세스할 수 있을 때까지 기다려야 하는 경우 (예를 들어 데이터를 파일에 쓸 수 있으려면 통신 포트에서 수신 해야 함)

   그렇다면를 사용 `CEvent` 합니다.

2. 같은 응용 프로그램 내에서 한 번에 두 개 이상의 스레드가이 리소스에 액세스할 수 있습니다. 예를 들어 응용 프로그램에서 동일한 문서에 대 한 뷰가 포함 된 최대 5 개의 창을 사용할 수 있나요?

   그렇다면를 사용 `CSemaphore` 합니다.

3. 이 리소스를 사용 하는 응용 프로그램이 두 개 이상 있을 수 있습니다 (예: 리소스가 DLL에 있는 경우).

   그렇다면를 사용 `CMutex` 합니다.

   그렇지 않으면를 사용 `CCriticalSection` 합니다.

`CSyncObject` 는 직접 사용 되지 않습니다. 이 클래스는 다른 4 개의 동기화 클래스에 대 한 기본 클래스입니다.

## <a name="example-1-using-three-synchronization-classes"></a>예제 1: 세 개의 동기화 클래스 사용

예를 들어 연결 된 계정 목록을 유지 관리 하는 응용 프로그램을 사용 합니다. 이 응용 프로그램은 별도의 창에서 최대 3 개의 계정을 검사할 수 있지만 특정 시간에 하나만 업데이트할 수 있습니다. 계정이 업데이트 되 면 업데이트 된 데이터가 네트워크를 통해 데이터 보관에 전송 됩니다.

이 예제 응용 프로그램에서는 세 가지 유형의 동기화 클래스를 모두 사용 합니다. 최대 3 개의 계정을 한 번에 검사할 수 있으므로를 사용 `CSemaphore` 하 여 세 개의 뷰 개체에 대 한 액세스를 제한 합니다. 네 번째 계정을 보려는 시도가 발생 하면 응용 프로그램은 처음 3 개의 windows 중 하나가 닫히거나 실패할 때까지 대기 합니다. 계정이 업데이트 되 면 응용 프로그램에서는를 사용 하 여 `CCriticalSection` 한 번에 하나의 계정만 업데이트 되도록 합니다. 업데이트에 성공 하면 이벤트가 신호를 받을 때까지 대기 하는 스레드를 해제 하는 신호를 보냅니다 `CEvent` . 이 스레드는 새 데이터를 데이터 보관 파일로 보냅니다.

## <a name="example-2-using-synchronization-access-classes"></a>예제 2: 동기화 액세스 클래스 사용

사용할 동기화 액세스 클래스를 선택 하는 것이 훨씬 더 간단 합니다. 응용 프로그램에서 단일 제어 리소스에만 액세스 하는 경우를 사용 `CSingleLock` 합니다. 제어 되는 리소스 중 하나에 액세스할 수 있어야 하는 경우를 사용 `CMultiLock` 합니다. 예 1에서는 `CSingleLock` 각 경우에 특정 시간에 하나의 리소스가 필요 하기 때문에가 사용 되었습니다.

동기화 클래스를 사용 하는 방법에 대 한 자세한 내용은 [다중 스레딩: 동기화 클래스 사용 방법](multithreading-how-to-use-the-synchronization-classes.md)을 참조 하세요. 동기화에 대 한 자세한 내용은 Windows SDK의 [동기화](/windows/win32/Sync/synchronization) 를 참조 하세요. MFC의 다중 스레딩 지원에 대 한 자세한 내용은 [c + + 및 mfc를 사용한 다중 스레딩](multithreading-with-cpp-and-mfc.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[C++ 및 MFC에서 다중 스레딩](multithreading-with-cpp-and-mfc.md)
