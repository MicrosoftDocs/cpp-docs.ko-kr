---
description: '자세한 정보: 다중 스레딩: MFC 프로그래밍 팁'
title: '다중 스레딩: MFC 프로그래밍 팁'
ms.date: 08/27/2018
helpviewer_keywords:
- multithreading [C++], programming tips
- handle maps [C++]
- access control [C++], multithreading
- objects [C++], multiple threads and
- non-MFC threads [C++]
- threading [MFC], programming tips
- critical sections [C++]
- synchronization [C++], multithreading
- programming [C++], multithreaded
- communications [C++], between threads
- threading [C++], best practices
- troubleshooting [C++], multithreading
- Windows handle maps [C++]
ms.assetid: ad14cc70-c91c-4c24-942f-13a75e58bf8a
ms.openlocfilehash: 5c7141462da21c6b9298f48ab85b3de06a039d08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149892"
---
# <a name="multithreading-mfc-programming-tips"></a>다중 스레딩: MFC 프로그래밍 팁

다중 스레드 응용 프로그램은 작업을 의도 된 순서로 수행 하 고 여러 스레드에서 액세스 하는 모든 데이터가 손상 되지 않도록 단일 스레드 응용 프로그램 보다 엄격한 주의가 필요 합니다. 이 항목에서는 MFC (Microsoft Foundation Class) 라이브러리를 사용 하 여 다중 스레드 응용 프로그램을 프로그래밍할 때 잠재적인 문제를 방지 하는 기술에 대해 설명 합니다

- [여러 스레드에서 개체 액세스](#_core_accessing_objects_from_multiple_threads)

- [비 MFC 스레드에서 MFC 개체 액세스](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)

- [Windows 핸들 맵](#_core_windows_handle_maps)

- [스레드 간 통신](#_core_communicating_between_threads)

## <a name="accessing-objects-from-multiple-threads"></a><a name="_core_accessing_objects_from_multiple_threads"></a> 여러 스레드에서 개체 액세스

MFC 개체는 독립적으로 스레드로부터 안전 하지 않습니다. MFC 동기화 클래스 및/또는 적절 한 Win32 동기화 개체 (예: 임계 영역)를 사용 하지 않는 한 별도의 두 스레드는 동일한 개체를 조작할 수 없습니다. 임계 영역 및 기타 관련 개체에 대 한 자세한 내용은 Windows SDK의 [동기화](/windows/win32/Sync/synchronization) 를 참조 하세요.

클래스 라이브러리는 내부적으로 중요 한 섹션을 사용 하 여 디버그 메모리 할당에서 사용 되는 것과 같은 전역 데이터 구조를 보호 합니다.

## <a name="accessing-mfc-objects-from-non-mfc-threads"></a><a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> 비 MFC 스레드에서 MFC 개체 액세스

[CWinThread](../mfc/reference/cwinthread-class.md) 개체를 사용 하는 것 외에 다른 방식으로 스레드를 만드는 다중 스레드 응용 프로그램이 있는 경우 해당 스레드에서 다른 MFC 개체에 액세스할 수 없습니다. 즉, 보조 스레드에서 MFC 개체에 액세스 하려는 경우 [다중 스레딩: User-Interface 스레드 만들기](multithreading-creating-user-interface-threads.md) 또는 [다중 스레딩: 작업자 스레드 만들기](multithreading-creating-worker-threads.md)에 설명 된 메서드 중 하나를 사용 하 여 해당 스레드를 만들어야 합니다. 이러한 메서드는 클래스 라이브러리가 다중 스레드 응용 프로그램을 처리 하는 데 필요한 내부 변수를 초기화할 수 있는 유일한 방법입니다.

## <a name="windows-handle-maps"></a><a name="_core_windows_handle_maps"></a> Windows 핸들 맵

일반적으로 스레드는 만든 MFC 개체에만 액세스할 수 있습니다. 이는 여러 스레드에서 동시에 액세스 하는 것을 방지 하기 위해 임시 및 영구 Windows 핸들 맵이 스레드 로컬 저장소에 유지 되기 때문입니다. 예를 들어 작업자 스레드가 계산을 수행한 다음 문서의 멤버 함수를 호출 하 여 `UpdateAllViews` 새 데이터에 대 한 뷰를 포함 하는 창을 만들 수는 없습니다. `CWnd`개체에서 hwnd로의 맵은 주 스레드에 로컬인 것 이기 때문에이 방법은 전혀 영향을 주지 않습니다. 즉, 한 스레드가 Windows 핸들에서 c + + 개체로 매핑될 수 있지만 다른 스레드에서 동일한 핸들을 다른 c + + 개체에 매핑할 수 있습니다. 한 스레드에서 변경한 내용은 다른 스레드에서 반영 되지 않습니다.

이 문제를 해결 하는 방법에는 여러 가지가 있습니다. 첫 번째는 c + + 개체가 아닌 HWND와 같은 개별 핸들을 작업자 스레드에 전달 하는 것입니다. 그런 다음 작업자 스레드는 적절 한 멤버 함수를 호출 하 여 이러한 개체를 임시 맵에 추가 합니다 `FromHandle` . 를 호출 하 여 스레드의 영구 맵에 개체를 추가할 수도 `Attach` 있지만,이 작업은 개체가 스레드 보다 더 오래 존재 하는 것으로 보장 되는 경우에만 수행 해야 합니다.

또 다른 방법은 작업자 스레드가 수행 하는 여러 태스크에 해당 하는 사용자 정의 메시지를 새로 만들고를 사용 하 여 응용 프로그램의 주 창에 이러한 메시지를 게시 하는 것입니다 `::PostMessage` . 이 통신 방법은 두 스레드가 동일한 주소 공간에서 실행 되는 경우를 제외 하 고 두 개의 서로 다른 응용 프로그램과 유사 합니다.

핸들 맵에 대 한 자세한 내용은 [Technical Note 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md)을 참조 하세요. 스레드 로컬 저장소에 대 한 자세한 내용은 [스레드 로컬 저장소](/windows/win32/ProcThread/thread-local-storage) 및 Windows SDK [스레드 로컬 저장소 사용](/windows/win32/ProcThread/using-thread-local-storage) 을 참조 하세요.

## <a name="communicating-between-threads"></a><a name="_core_communicating_between_threads"></a> 스레드 간 통신

MFC는 스레드가 개체에 대 한 액세스를 동기화 하 여 스레드 보안을 유지할 수 있도록 하는 다양 한 클래스를 제공 합니다. 이러한 클래스를 사용 하는 방법에 대 한 자세한 내용은 [다중 스레딩: 동기화 클래스](multithreading-how-to-use-the-synchronization-classes.md) 및 다중 스레딩을 사용 하는 방법 [: 동기화 클래스를 사용 하는 경우를](multithreading-when-to-use-the-synchronization-classes.md)참조 하세요. 이러한 개체에 대 한 자세한 내용은 Windows SDK의 [동기화](/windows/win32/Sync/synchronization) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[C++ 및 MFC에서 다중 스레딩](multithreading-with-cpp-and-mfc.md)
