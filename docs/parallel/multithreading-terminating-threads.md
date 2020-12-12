---
description: '자세한 정보: 다중 스레딩: MFC의 스레드 종료'
title: '다중 스레딩: MFC에서 스레드 종료'
ms.date: 08/27/2018
helpviewer_keywords:
- premature thread termination
- starting threads
- threading [MFC], terminating threads
- multithreading [C++], terminating threads
- threading [C++], stopping threads
- terminating threads
- stopping threads
- AfxEndThread method
ms.assetid: 4c0a8c6d-c02f-456d-bd02-0a8c8d006ecb
ms.openlocfilehash: dc353bc0edf14d718ee11e140fca11e4c0545588
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149879"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>다중 스레딩: MFC에서 스레드 종료

두 가지 일반적인 경우는 스레드를 종료 합니다. 즉, 제어 함수가 종료 되거나 스레드가 완료 될 때까지 실행 될 수 없습니다. 워드 프로세서에서 백그라운드 인쇄를 위해 스레드를 사용 하는 경우 인쇄가 성공적으로 완료 되 면 제어 함수는 정상적으로 종료 됩니다. 그러나 사용자가 인쇄를 취소 하려는 경우 백그라운드 인쇄 스레드를 중간에 종료 해야 합니다. 이 항목에서는 각 상황을 구현 하는 방법과 스레드가 종료 된 후의 종료 코드를 가져오는 방법에 대해 설명 합니다.

- [정상적인 스레드 종료](#_core_normal_thread_termination)

- [중간 스레드 종료](#_core_premature_thread_termination)

- [스레드의 종료 코드 검색](#_core_retrieving_the_exit_code_of_a_thread)

## <a name="normal-thread-termination"></a><a name="_core_normal_thread_termination"></a> 정상적인 스레드 종료

작업자 스레드의 경우 일반적인 스레드 종료는 간단 합니다. 제어 함수를 종료 하 고 종료 이유를 나타내는 값을 반환 합니다. [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) 함수 또는 문을 사용할 수 있습니다 **`return`** . 일반적으로 0은 성공적인 완료를 나타냅니다.

사용자 인터페이스 스레드의 경우 프로세스는 간단 합니다. 사용자 인터페이스 스레드 내에서 Windows SDK의 [PostQuitMessage](/windows/win32/api/winuser/nf-winuser-postquitmessage) 를 호출 합니다. 에서 사용 하는 유일한 매개 변수는 `PostQuitMessage` 스레드의 종료 코드입니다. 작업자 스레드의 경우 0은 일반적으로 성공적으로 완료 되었음을 나타냅니다.

## <a name="premature-thread-termination"></a><a name="_core_premature_thread_termination"></a> 중간 스레드 종료

스레드를 중간에 종료 하는 것은 거의 간단 합니다. 스레드 내에서 [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) 를 호출 합니다. 원하는 종료 코드를 유일한 매개 변수로 전달 합니다. 이렇게 하면 스레드 실행을 중지 하 고, 스레드의 스택을 할당 취소 하 고, 스레드에 연결 된 모든 Dll을 분리 하 고, 메모리에서 스레드 개체를 삭제 합니다.

`AfxEndThread` 종료 될 스레드 내에서를 호출 해야 합니다. 다른 스레드에서 스레드를 종료 하려는 경우 두 스레드 간에 통신 메서드를 설정 해야 합니다.

## <a name="retrieving-the-exit-code-of-a-thread"></a><a name="_core_retrieving_the_exit_code_of_a_thread"></a> 스레드의 종료 코드 검색

작업자 또는 사용자 인터페이스 스레드의 종료 코드를 가져오려면 [Getexitcodethread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread) 함수를 호출 합니다. 이 함수에 대 한 자세한 내용은 Windows SDK를 참조 하세요. 이 함수는 개체의 데이터 멤버에 저장 된 스레드에 대 `m_hThread` `CWinThread` 한 핸들 및 DWORD 주소를 사용 합니다.

스레드가 아직 활성 상태인 경우 `GetExitCodeThread` 제공 된 DWORD 주소에 STILL_ACTIVE를 배치 하 고, 그렇지 않은 경우에는 종료 코드가이 주소에 배치 됩니다.

[CWinThread](../mfc/reference/cwinthread-class.md) 개체의 종료 코드를 검색 하면 추가 단계가 필요 합니다. 기본적으로 `CWinThread` 스레드가 종료 되 면 스레드 개체가 삭제 됩니다. 즉, `m_hThread` `CWinThread` 개체가 더 이상 존재 하지 않으므로 데이터 멤버에 액세스할 수 없습니다. 이러한 상황을 방지 하려면 다음 중 하나를 수행 합니다.

- `m_bAutoDelete`데이터 멤버를 FALSE로 설정 합니다. 이렇게 하면 `CWinThread` 스레드가 종료 된 후에도 개체를 계속 사용할 수 있습니다. 그런 다음 `m_hThread` 스레드가 종료 된 후에 데이터 멤버에 액세스할 수 있습니다. 그러나이 방법을 사용 하는 경우 `CWinThread` 프레임 워크에서 자동으로 삭제 하지 않으므로 개체를 소멸 해야 합니다. 이는 선호되는 방법입니다.

- 스레드의 핸들을 별도로 저장 합니다. 스레드를 만든 후에 `m_hThread` 는를 사용 하 여 데이터 멤버를 `::DuplicateHandle` 다른 변수에 복사 하 고 해당 변수를 통해 액세스 합니다. 이러한 방식으로 종료가 발생 하면 개체가 자동으로 삭제 되 고 스레드가 종료 된 이유를 확인할 수 있습니다. 핸들을 복제 하려면 스레드가 종료 되지 않도록 주의 해야 합니다. 이 작업을 수행 하는 가장 안전한 방법은 [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)에 CREATE_SUSPENDED를 전달 하 고, 핸들을 저장 한 다음 [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread)를 호출 하 여 스레드를 다시 시작 하는 것입니다.

어느 방법을 사용 하 든 개체가 종료 되는 이유를 확인할 수 있습니다 `CWinThread` .

## <a name="see-also"></a>참고 항목

[C++ 및 MFC에서 다중 스레딩](multithreading-with-cpp-and-mfc.md)<br/>
[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread)
