---
description: '방법에 대 한 자세한 정보: 방법: 정기적으로 메시지 보내기'
title: '방법: 정기적으로 메시지 보내기'
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: f65226d8101ddbadaee97a16f63512b9c8dcb41e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197286"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>방법: 정기적으로 메시지 보내기

이 예제에서는 concurrency::[timer 클래스](../../parallel/concrt/reference/timer-class.md) 를 사용 하 여 일정 한 간격으로 메시지를 보내는 방법을 보여 줍니다.

## <a name="example"></a>예제

다음 예제에서는 개체를 사용 하 여 `timer` 시간이 오래 걸리는 작업 중에 진행률을 보고 합니다. 이 예제에서는 `timer` 개체를 [concurrency:: call](../../parallel/concrt/reference/call-class.md) 개체에 연결 합니다. `call`개체는 일정 한 간격으로 진행률 표시기를 콘솔에 출력 합니다. [Concurrency:: timer:: start](reference/timer-class.md#start) 메서드는 별도의 컨텍스트에서 타이머를 실행 합니다. `perform_lengthy_operation`함수는 주 컨텍스트에서 [concurrency:: wait](reference/concurrency-namespace-functions.md#wait) 함수를 호출 하 여 시간이 오래 걸리는 작업을 시뮬레이트합니다.

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

이 예제에서는 다음과 같은 샘플 출력을 생성 합니다.

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `report-progress.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc report-progress**

## <a name="see-also"></a>참고 항목

[비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[메시지 전달 함수](../../parallel/concrt/message-passing-functions.md)
