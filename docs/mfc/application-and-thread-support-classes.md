---
description: '자세히 알아보기: 응용 프로그램 및 스레드 지원 클래스'
title: 애플리케이션 및 스레드 지원 클래스
ms.date: 11/04/2016
f1_keywords:
- vc.classes.support
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
ms.openlocfilehash: 89ab6e324a777c272dcbcfabc746c03cb6731589
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176745"
---
# <a name="application-and-thread-support-classes"></a>애플리케이션 및 스레드 지원 클래스

각 응용 프로그램에는 하나의 응용 프로그램 개체만 있습니다. 이 개체는 실행 중인 프로그램의 다른 개체를 조정 하며에서 파생 됩니다 `CWinApp` .

MFC (Microsoft Foundation Class) 라이브러리는 응용 프로그램 내에서 여러 실행 스레드를 지원 합니다. 모든 응용 프로그램에는 스레드가 하나 이상 있어야 합니다. 개체에서 사용 하는 스레드는 `CWinApp` 이 주 스레드입니다.

`CWinThread` 운영 체제의 스레딩 기능 일부를 캡슐화 합니다. 여러 스레드를 더 쉽게 사용 하기 위해 MFC는 Win32 동기화 개체에 c + + 인터페이스를 제공 하는 동기화 개체 클래스도 제공 합니다.

## <a name="application-and-thread-classes"></a>응용 프로그램 및 스레드 클래스

[CWinApp](reference/cwinapp-class.md)<br/>
응용 프로그램을 초기화, 실행 및 종료 하는 코드를 캡슐화 합니다. 이 클래스에서 응용 프로그램 개체를 파생 합니다.

[CWinThread](reference/cwinthread-class.md)<br/>
모든 스레드에 대 한 기본 클래스입니다. 을 직접 사용 하거나 `CWinThread` 스레드에서 사용자 인터페이스 함수를 수행 하는 경우에서 클래스를 파생 시킵니다. `CWinApp`는 `CWinThread`에서 파생됩니다.

## <a name="synchronization-object-classes"></a>동기화 개체 클래스

[CSyncObject](reference/csyncobject-class.md)<br/>
동기화 개체 클래스의 기본 클래스입니다.

[CCriticalSection](reference/ccriticalsection-class.md)<br/>
단일 프로세스 내에서 하나의 스레드만 개체에 액세스할 수 있도록 하는 동기화 클래스입니다.

[CSemaphore](reference/csemaphore-class.md)<br/>
하나 및 지정 된 최대 수의 개체에 동시에 액세스할 수 있는 동기화 클래스입니다.

[CMutex](reference/cmutex-class.md)<br/>
여러 프로세스에서 하나의 스레드만 개체에 액세스할 수 있도록 하는 동기화 클래스입니다.

[CEvent](reference/cevent-class.md)<br/>
이벤트가 발생 했을 때 응용 프로그램에 알리는 동기화 클래스입니다.

[CSingleLock](reference/csinglelock-class.md)<br/>
스레드 보호 클래스의 멤버 함수에서 하나의 동기화 개체를 잠그기 위해 사용 됩니다.

[CMultiLock](reference/cmultilock-class.md)<br/>
스레드로부터 안전한 클래스의 멤버 함수에서 동기화 개체의 배열에서 하나 이상의 동기화 개체를 잠그기 위해 사용 됩니다.

## <a name="related-classes"></a>관련 클래스

[CCommandLineInfo](reference/ccommandlineinfo-class.md)<br/>
프로그램이 시작 된 명령줄을 구문 분석 합니다.

[CWaitCursor](reference/cwaitcursor-class.md)<br/>
대기 커서를 화면에 배치 합니다. 시간이 오래 걸리는 작업 중에 사용 됩니다.

[CDockState](reference/cdockstate-class.md)<br/>
컨트롤 막대에 대 한 고정 상태 데이터의 영구 저장소를 처리 합니다.

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
가장 최근에 사용한 (MRU) 파일 목록을 유지 관리 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
