---
description: '자세히 알아보기: C 및 Win32를 사용 하는 다중 스레딩'
title: C 및 Wind32를 사용한 다중 스레딩
ms.date: 08/09/2019
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
ms.openlocfilehash: cde6166f071035edd4aa0a07f578c6e3b66a0c21
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149827"
---
# <a name="multithreading-with-c-and-win32"></a>C 및 Wind32를 사용한 다중 스레딩

Microsoft C/c + + 컴파일러 (MSVC)는 다중 스레드 응용 프로그램을 만들기 위한 지원을 제공 합니다. 응용 프로그램에서 사용자 인터페이스가 응답 하지 않게 하는 부담이 큰 작업을 수행 해야 하는 경우 둘 이상의 스레드를 사용 하는 것이 좋습니다.

MSVC를 사용 하면 여러 스레드를 사용 하 여 프로그래밍 하는 데 여러 가지 방법이 있습니다. c + +/WinRT 및 Windows 런타임 라이브러리, MFC (Microsoft Foundation Class) 라이브러리, c + +/CLI 및 .NET 런타임, C 런타임 라이브러리 및 Win32 API 사용할 수 있습니다. 이 문서는 C의 다중 스레딩에 대 한 것입니다. 예제 코드는 [C에서 샘플 다중 스레드 프로그램](sample-multithread-c-program.md)을 참조 하세요.

## <a name="multithread-programs"></a>다중 스레드 프로그램

스레드는 기본적으로 프로그램을 통한 실행 경로입니다. Win32에서 예약 하는 가장 작은 실행 단위 이기도 합니다. 스레드는 스택, CPU 등록 상태, 시스템 스케줄러의 실행 목록에 있는 항목으로 구성 됩니다. 각 스레드는 모든 프로세스의 리소스를 공유 합니다.

프로세스는 하나 이상의 스레드와 메모리 내 프로그램의 코드, 데이터 및 기타 리소스로 구성 됩니다. 일반적인 프로그램 리소스는 열린 파일, 세마포 및 동적으로 할당 된 메모리입니다. 시스템 스케줄러가 스레드 실행 제어 중 하나를 제공 하면 프로그램이 실행 됩니다. 스케줄러는 실행할 스레드와 실행 시기를 결정 합니다. 우선 순위가 낮은 스레드는 우선 순위가 높은 스레드가 해당 작업을 완료 하는 동안 대기 해야 할 수 있습니다. 다중 프로세서 컴퓨터에서 스케줄러는 개별 스레드를 서로 다른 프로세서로 이동 하 여 CPU 부하를 분산 시킬 수 있습니다.

프로세스의 각 스레드는 독립적으로 작동 합니다. 서로 표시 하지 않는 한 스레드는 개별적으로 실행 되며 프로세스의 다른 스레드를 인식 하지 못합니다. 그러나 공용 리소스를 공유 하는 스레드는 세마포 또는 다른 프로세스간 통신 방법을 사용 하 여 작업을 조정 해야 합니다. 스레드를 동기화 하는 방법에 대 한 자세한 내용은 [다중 스레드 Win32 프로그램 작성](#writing-a-multithreaded-win32-program)을 참조 하세요.

## <a name="library-support-for-multithreading"></a>다중 스레딩을 위한 라이브러리 지원

모든 버전의 CRT는 이제 일부 함수의 잠기지 않은 버전을 제외 하 고 다중 스레딩을 지원 합니다. 자세한 내용은 [다중 스레드 라이브러리 성능](../c-runtime-library/multithreaded-libraries-performance.md)을 참조 하세요. 코드와 연결 하는 데 사용할 수 있는 CRT 버전에 대 한 자세한 내용은 [crt 라이브러리 기능](../c-runtime-library/crt-library-features.md)을 참조 하세요.

## <a name="include-files-for-multithreading"></a>다중 스레딩을 위한 포함 파일

표준 CRT 포함 파일은 라이브러리에서 구현 되는 C 런타임 라이브러리 함수를 선언 합니다. 컴파일러 옵션에서 [__fastcall 또는 __vectorcall](../build/reference/gd-gr-gv-gz-calling-convention.md) 호출 규칙을 지정 하는 경우 컴파일러는 모든 함수를 등록 호출 규칙을 사용 하 여 호출 해야 한다고 가정 합니다. 런타임 라이브러리 함수는 C 호출 규칙을 사용 하 고 표준 포함 파일의 선언은 이러한 함수에 대 한 올바른 외부 참조를 생성 하도록 컴파일러에 지시 합니다.

## <a name="crt-functions-for-thread-control"></a>스레드 컨트롤에 대 한 CRT 함수

모든 Win32 프로그램에는 하나 이상의 스레드가 있습니다. 모든 스레드에서 추가 스레드를 만들 수 있습니다. 스레드는 작업을 신속 하 게 완료 한 후 종료 하거나 프로그램의 수명 동안 활성 상태로 유지할 수 있습니다.

CRT 라이브러리는 스레드를 만들고 종료 하기 위해 [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md), [_endthread 및 _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)함수를 제공 합니다.

`_beginthread`및 `_beginthreadex` 함수는 새 스레드를 만들고 작업이 성공한 경우 스레드 식별자를 반환 합니다. 스레드는 실행이 완료 되 면 자동으로 종료 됩니다. 또는 또는에 대 한 호출을 사용 하 여 자신을 종료할 수 있습니다 `_endthread` `_endthreadex` .

> [!NOTE]
> Libcmt.lib를 사용 하 여 빌드된 프로그램에서 C 런타임 루틴을 호출 하는 경우 또는 함수를 사용 하 여 스레드를 시작 해야 합니다 `_beginthread` `_beginthreadex` . Win32 함수 및를 사용 하지 `ExitThread` 마십시오 `CreateThread` . 를 사용 하면 `SuspendThread` 일시 중단 된 스레드가 C 런타임 데이터 구조에 대 한 액세스를 완료할 때까지 대기 하는 두 개 이상의 스레드가 차단 될 때 교착 상태가 발생할 수 있습니다.

### <a name="the-_beginthread-and-_beginthreadex-functions"></a><a name="_core_the__beginthread_function"></a> _Beginthread 및 _beginthreadex 함수

`_beginthread`및 `_beginthreadex` 함수는 새 스레드를 만듭니다. 스레드는 프로세스의 코드 및 데이터 세그먼트를 프로세스의 다른 스레드와 공유 하지만 고유한 레지스터 값, 스택 공간 및 현재 명령 주소를 포함 합니다. 시스템은 프로세스의 모든 스레드가 동시에 실행 될 수 있도록 각 스레드에 CPU 시간을 제공 합니다.

`_beginthread` 및 `_beginthreadex` 는 Win32 API의 [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) 함수와 비슷하지만 다음과 같은 차이점이 있습니다.

- 특정 C 런타임 라이브러리 변수를 초기화 합니다. 이는 스레드에서 C 런타임 라이브러리를 사용 하는 경우에만 중요 합니다.

- `CreateThread` 보안 특성에 대 한 제어를 제공 합니다. 이 함수를 사용 하 여 일시 중단 된 상태의 스레드를 시작할 수 있습니다.

`_beginthread``_beginthreadex`는 성공 하면 새 스레드에 대 한 핸들을 반환 하 고 오류가 발생 한 경우 오류 코드를 반환 합니다.

### <a name="the-_endthread-and-_endthreadex-functions"></a><a name="_core_the__endthread_function"></a> _Endthread 및 _endthreadex 함수

[_Endthread](../c-runtime-library/reference/endthread-endthreadex.md) 함수는로 만든 스레드를 종료 하 `_beginthread` 고, 마찬가지로에서 `_endthreadex` 만든 스레드를 종료 `_beginthreadex` 합니다. 스레드는 완료 될 때 자동으로 종료 됩니다. `_endthread` 및 `_endthreadex` 는 스레드 내에서 조건부 종료에 유용 합니다. 통신 포트의 제어를 받을 수 없는 경우와 같이 통신 처리 전용 스레드를 종료할 수 있습니다.

## <a name="writing-a-multithreaded-win32-program"></a>다중 스레드 Win32 프로그램 작성

여러 스레드가 포함 된 프로그램을 작성 하는 경우 [프로그램의 리소스의 동작과 사용](#_core_sharing_common_resources_between_threads)을 조정 해야 합니다. 또한 각 스레드가 [자체 스택을](#_core_thread_stacks)수신 하는지 확인 합니다.

### <a name="sharing-common-resources-between-threads"></a><a name="_core_sharing_common_resources_between_threads"></a> 스레드 간 공통 리소스 공유

> [!NOTE]
> MFC 관점에서의 비슷한 논의는 [다중 스레딩: 프로그래밍 팁](multithreading-programming-tips.md) 과 [다중 스레딩: 동기화 클래스를 사용 하는 경우를](multithreading-when-to-use-the-synchronization-classes.md)참조 하세요.

각 스레드에는 자체 스택과 CPU 레지스터의 자체 복사본이 있습니다. 파일, 정적 데이터 및 힙 메모리와 같은 기타 리소스는 프로세스의 모든 스레드에서 공유 됩니다. 이러한 공통 리소스를 사용 하는 스레드는 동기화 되어야 합니다. Win32에서는 세마포, 임계 영역, 이벤트 및 뮤텍스를 비롯 한 리소스를 동기화 하는 여러 가지 방법을 제공 합니다.

여러 스레드가 정적 데이터에 액세스 하는 경우에는 프로그램에서 가능한 리소스 충돌을 제공 해야 합니다. 한 스레드가 다른 스레드에 표시 되는 항목에 대 한 *x*,*y* 좌표를 포함 하는 정적 데이터 구조를 업데이트 하는 프로그램을 고려 합니다. 업데이트 스레드가 *x* 좌표를 변경 하 고 *y* 좌표를 변경 하기 전에 선점 되는 경우 *y* 좌표를 업데이트 하기 전에 표시 스레드를 예약할 수 있습니다. 항목이 잘못 된 위치에 표시 됩니다. 세마포를 사용 하 여 구조에 대 한 액세스를 제어 하면이 문제를 방지할 수 있습니다.

뮤텍스 (short *mut* ual *ex* clusion)는 서로 비동기적으로 실행 되는 스레드나 프로세스 간에 통신 하는 방법입니다. 이 통신은 일반적으로 리소스를 잠그고 잠금 해제 하 여 공유 리소스에 대 한 액세스를 제어 함으로써 여러 스레드 또는 프로세스의 작업을 조정 하는 데 사용할 수 있습니다. 이 *x*,*y* 좌표 업데이트 문제를 해결 하기 위해 업데이트 스레드는 업데이트를 수행 하기 전에 데이터 구조가 사용 중임을 나타내는 뮤텍스를 설정 합니다. 두 좌표가 모두 처리 된 후에 뮤텍스를 지웁니다. 디스플레이 스레드는 표시를 업데이트 하기 전에 뮤텍스를 지울 때까지 기다려야 합니다. 뮤텍스를 대기 하는이 프로세스를 종종 뮤텍스를 *차단* 이라고 합니다 .이 프로세스는 중단 되 고 뮤텍스를 지울 때까지 계속할 수 없기 때문입니다.

[샘플 다중 스레드 c 프로그램](sample-multithread-c-program.md) 에 표시 된 바운스 프로그램은 라는 뮤텍스를 사용 하 여 `ScreenMutex` 화면 업데이트를 조정 합니다. 표시 스레드 중 하나를 화면에 쓸 준비가 될 때마다는 핸들을 사용 하 여 `WaitForSingleObject` 를 호출 하 고, 무한 무한은 호출을 사용 하 여 뮤텍스를 차단 하 `ScreenMutex` `WaitForSingleObject` 고 시간 제한이 없음을 나타냅니다. `ScreenMutex` 가 명확 하지 않은 경우 wait 함수는 다른 스레드가 표시를 방해할 수 없도록 뮤텍스를 설정 하 고 스레드 실행을 계속 합니다. 그렇지 않으면 뮤텍스를 지울 때까지 스레드가 차단 됩니다. 스레드가 표시 업데이트를 완료 하면를 호출 하 여 뮤텍스를 해제 합니다 `ReleaseMutex` .

화면이 표시 되 고 정적 데이터는 신중 하 게 관리 해야 하는 리소스 중 두 가지입니다. 예를 들어 프로그램에 동일한 파일에 액세스 하는 스레드가 여러 개 있을 수 있습니다. 다른 스레드가 파일 포인터를 이동 했을 수 있으므로 각 스레드는 읽기 또는 쓰기 전에 파일 포인터를 다시 설정 해야 합니다. 또한 각 스레드는 포인터가 배치 된 시간과 파일에 액세스 하는 시간 사이에 선점 되지 않는지 확인 해야 합니다. 이러한 스레드는를 사용 하 여 각 파일에 액세스 하 고를 호출 하 여 bracketing 파일에 대 한 액세스를 조정 해야 합니다 `WaitForSingleObject` `ReleaseMutex` . 다음 코드 예제에서는이 방법을 보여 줍니다.

```C
HANDLE    hIOMutex = CreateMutex (NULL, FALSE, NULL);

WaitForSingleObject( hIOMutex, INFINITE );
fseek( fp, desired_position, 0L );
fwrite( data, sizeof( data ), 1, fp );
ReleaseMutex( hIOMutex);
```

### <a name="thread-stacks"></a><a name="_core_thread_stacks"></a> 스레드 스택

응용 프로그램의 기본 스택 공간은 스레드 1 이라고 하는 실행의 첫 번째 스레드에 할당 됩니다. 따라서 프로그램에 필요한 각 추가 스레드에 대해 별도의 스택에 할당할 메모리 크기를 지정 해야 합니다. 필요한 경우 운영 체제에서 스레드에 추가 스택 공간을 할당 하지만 기본값을 지정 해야 합니다.

호출의 첫 번째 인수는 스레드를 실행 하는 `_beginthread` 함수에 대 한 포인터입니다 `BounceProc` . 두 번째 인수는 스레드의 기본 스택 크기를 지정 합니다. 마지막 인수는에 전달 되는 ID 번호입니다 `BounceProc` . `BounceProc` 는 ID 번호를 사용 하 여 난수 생성기의 초기값을 가져오고 스레드의 색 특성과 표시 문자를 선택 합니다.

C 런타임 라이브러리 또는 Win32 API에 대 한 호출을 수행 하는 스레드는 호출 하는 라이브러리 및 API 함수에 대해 충분 한 스택 공간을 허용 해야 합니다. C 함수에는 `printf` 500 바이트 이상의 스택 공간이 필요 하며 Win32 API 루틴을 호출할 때 2k 바이트의 스택 공간을 사용할 수 있어야 합니다.

각 스레드에는 자체 스택이 있으므로 가능한 적은 수의 정적 데이터로를 사용 하 여 데이터 항목에 대 한 잠재적 충돌을 방지할 수 있습니다. 스레드에 전용으로 사용할 수 있는 모든 데이터에 대해 자동 스택 변수를 사용 하도록 프로그램을 디자인 합니다. 바운스 프로그램의 유일한 전역 변수는 초기화 된 후 변경 되지 않는 뮤텍스 또는 변수 중 하나입니다.

또한 Win32는 스레드 단위 데이터를 저장 하는 TLS (스레드 로컬 저장소)를 제공 합니다. 자세한 내용은 [TLS (스레드 로컬 저장소)](thread-local-storage-tls.md)를 참조 하세요.

## <a name="avoiding-problem-areas-with-multithread-programs"></a>다중 스레드 프로그램으로 문제 영역 방지

다중 스레드 C 프로그램을 만들거나 연결 하거나 실행 하는 동안 발생할 수 있는 몇 가지 문제가 있습니다. 다음 표에서는 일반적인 몇 가지 문제에 대해 설명 합니다. (MFC 관점에서 유사한 논의는 [다중 스레딩: 프로그래밍 팁](multithreading-programming-tips.md)을 참조 하세요.)

|문제|가능한 원인:|
|-------------|--------------------|
|프로그램에서 보호 위반이 발생 했음을 나타내는 메시지 상자가 표시 됩니다.|많은 Win32 프로그래밍 오류로 인해 보호 위반이 발생 합니다. 보호 위반의 일반적인 원인은 null 포인터에 데이터를 간접적으로 할당 하는 것입니다. 프로그램에서이 파일에 속하지 않는 메모리에 액세스 하려고 하기 때문에 보호 위반이 발생 합니다.<br /><br /> 보호 위반의 원인을 검색 하는 쉬운 방법은 디버깅 정보를 사용 하 여 프로그램을 컴파일한 후 Visual Studio 환경에서 디버거를 통해 실행 하는 것입니다. 보호 오류가 발생 하면 Windows는 컨트롤을 디버거로 전송 하 고 커서는 문제의 원인이 되는 줄에 배치 됩니다.|
|프로그램에서 많은 컴파일 및 링크 오류를 생성 합니다.|컴파일러의 경고 수준을 가장 높은 값 중 하나로 설정 하 고 경고 메시지를 heeding 하 여 여러 잠재적 문제를 제거할 수 있습니다. 수준 3 또는 수준 4 경고 수준 옵션을 사용 하면 의도 하지 않은 데이터 변환, 누락 된 함수 프로토타입 및 ANSI 이외의 기능 사용을 검색할 수 있습니다.|

## <a name="see-also"></a>참고 항목

[이전 코드에 대 한 다중 스레딩 지원 (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)\
[C의 샘플 다중 스레드 프로그램](sample-multithread-c-program.md)\
[TLS (스레드 로컬 저장소)](thread-local-storage-tls.md)\
[C + +/WinRT를 사용한 동시성 및 비동기 작업](/windows/uwp/cpp-and-winrt-apis/concurrency)\
[C++ 및 MFC에서 다중 스레딩](multithreading-with-cpp-and-mfc.md)
