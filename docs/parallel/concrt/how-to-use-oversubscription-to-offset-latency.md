---
description: '자세한 정보: 방법: 초과 구독을 사용 하 여 대기 시간 오프셋'
title: '방법: 초과 구독을 사용하여 대기 오프셋'
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
ms.openlocfilehash: ec7b96703da2cbbe8a4d3caac3bfb1a1ff6f602a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341570"
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>방법: 초과 구독을 사용하여 대기 오프셋

초과 구독은 대기 시간이 긴 작업을 포함 하는 일부 응용 프로그램의 전체 효율성을 향상 시킬 수 있습니다. 이 항목에서는 초과 구독을 사용 하 여 네트워크 연결에서 데이터를 읽는 경우 발생 하는 대기 시간을 오프셋 하는 방법을 보여 줍니다.

## <a name="example"></a>예제

이 예제에서는 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md) 를 사용 하 여 HTTP 서버에서 파일을 다운로드 합니다. `http_reader`클래스는 [concurrency:: agent](../../parallel/concrt/reference/agent-class.md) 에서 파생 되며 메시지 전달을 사용 하 여 다운로드할 URL 이름을 비동기적으로 읽습니다.

`http_reader`클래스는 [concurrency:: task_group](reference/task-group-class.md) 클래스를 사용 하 여 각 파일을 동시에 읽습니다. 각 작업은 매개 변수를로 설정 하 여 [concurrency:: Context:: Oversubscribe](reference/context-class.md#oversubscribe) 메서드를 호출 `_BeginOversubscription` 하 여 **`true`** 현재 컨텍스트에서 초과 구독을 사용 하도록 설정 합니다. 그런 다음 각 작업은 Microsoft Foundation Classes (MFC) [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 및 [CHttpFile](../../mfc/reference/chttpfile-class.md) 클래스를 사용 하 여 파일을 다운로드 합니다. 마지막으로 각 작업 `Context::Oversubscribe` 은 `_BeginOversubscription` 매개 변수를로 설정 하 여를 호출 **`false`** 하 여 초과 구독을 비활성화 합니다.

초과 구독을 사용 하도록 설정 하면 런타임에서는 작업을 실행할 추가 스레드 하나를 만듭니다. 이러한 각 스레드는 현재 컨텍스트를 oversubscribe 추가 스레드를 만들 수도 있습니다. `http_reader`클래스는 [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) 개체를 사용 하 여 응용 프로그램에서 사용 하는 스레드 수를 제한 합니다. 에이전트는 고정 된 수의 토큰 값을 사용 하 여 버퍼를 초기화 합니다. 각 다운로드 작업에 대해 에이전트는 작업이 시작 되기 전에 버퍼에서 토큰 값을 읽은 다음 작업이 완료 된 후 해당 값을 다시 버퍼로 씁니다. 버퍼가 비어 있으면 에이전트는 다운로드 작업 중 하나가 버퍼에 값을 다시 쓸 때까지 기다립니다.

다음 예에서는 동시 작업의 수를 사용 가능한 하드웨어 스레드 수의 두 배로 제한 합니다. 이 값은 초과 구독을 시험해 볼 때 사용할 수 있는 좋은 시작 지점입니다. 특정 처리 환경에 맞는 값을 사용 하거나이 값을 동적으로 변경 하 여 실제 작업에 응답할 수 있습니다.

[!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]

이 예제에서는 4 개의 프로세서가 있는 컴퓨터에서 다음과 같은 출력을 생성 합니다.

```Output
Downloading http://www.adatum.com/...
Downloading http://www.adventure-works.com/...
Downloading http://www.alpineskihouse.com/...
Downloading http://www.cpandl.com/...
Downloading http://www.cohovineyard.com/...
Downloading http://www.cohowinery.com/...
Downloading http://www.cohovineyardandwinery.com/...
Downloading http://www.contoso.com/...
Downloading http://www.consolidatedmessenger.com/...
Downloading http://www.fabrikam.com/...
Downloading http://www.fourthcoffee.com/...
Downloading http://www.graphicdesigninstitute.com/...
Downloading http://www.humongousinsurance.com/...
Downloading http://www.litwareinc.com/...
Downloading http://www.lucernepublishing.com/...
Downloading http://www.margiestravel.com/...
Downloading http://www.northwindtraders.com/...
Downloading http://www.proseware.com/...
Downloading http://www.fineartschool.net...
Downloading http://www.tailspintoys.com/...
Downloaded 1801040 bytes in 3276 ms.
```

다른 태스크가 종료 될 때까지 대기 하는 동안 추가 작업이 실행 되기 때문에이 예제는 시간 초과를 사용 하도록 설정 하면 더 빨리 실행 될 수 있습니다.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `download-oversubscription.cpp` 후 **Visual Studio 명령 프롬프트** 창에서 다음 명령 중 하나를 실행 합니다.

```cmd
cl.exe /EHsc /MD /D "_AFXDLL" download-oversubscription.cpp
cl.exe /EHsc /MT download-oversubscription.cpp
```

## <a name="robust-programming"></a>강력한 프로그래밍

초과 구독을 더 이상 요구 하지 않는 경우 항상 사용 하지 않도록 설정 합니다. 다른 함수에서 throw 된 예외를 처리 하지 않는 함수를 고려 하십시오. 함수가 반환 되기 전에 초과 구독을 사용 하지 않도록 설정 하지 않으면 추가 병렬 작업도 현재 컨텍스트를 oversubscribe 됩니다.

RAII ( *리소스 획득) 초기화* (RAII) 패턴을 사용 하 여 지정 된 범위에 대 한 초과 구독을 제한할 수 있습니다. RAII 패턴에서 데이터 구조가 스택에 할당 됩니다. 해당 데이터 구조는 생성 될 때 리소스를 초기화 하거나 획득 하 고, 데이터 구조가 소멸 될 때 해당 리소스를 소멸 하거나 해제 합니다. RAII 패턴은 바깥쪽 범위가 끝나기 전에 소멸자가 호출 되도록 합니다. 따라서 예외가 throw 되거나 함수에 여러 문이 포함 된 경우 리소스가 올바르게 관리 됩니다 **`return`** .

다음 예에서는 이라는 구조체를 정의 합니다 `scoped_blocking_signal` . 구조체의 생성자는 `scoped_blocking_signal` 초과 구독을 사용 하도록 설정 하며 소멸자는 초과 구독을 사용 하지 않도록 설정 합니다.

[!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]

다음 예제에서는 `download` 메서드가 반환 되기 전에 RAII을 사용 하 여 초과 구독을 사용할 수 없도록 하기 위해 메서드 본문을 수정 합니다. 이 방법을 `download` 사용 하면 메서드가 예외를 안전 하 게 보호 합니다.

[!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]

## <a name="see-also"></a>참고 항목

[컨텍스트](../../parallel/concrt/contexts.md)<br/>
[Context::Oversubscribe 메서드](reference/context-class.md#oversubscribe)
