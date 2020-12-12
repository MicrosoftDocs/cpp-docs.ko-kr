---
description: '자세한 정보: 연습: 미래 구현'
title: '연습: 미래 구현'
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: b2ea0b273f25ce42f8b177ce2d8e4b4aef195109
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309227"
---
# <a name="walkthrough-implementing-futures"></a>연습: 미래 구현

이 항목에서는 응용 프로그램에서 퓨처를 구현 하는 방법을 보여 줍니다. 이 항목에서는 동시성 런타임의 기존 기능을 더 많은 항목으로 결합 하는 방법을 보여 줍니다.

> [!IMPORTANT]
> 이 항목에서는 이해를 돕기 위해 미래의 개념에 대해 설명합니다. 나중에 사용 하기 위해 값을 계산 하는 비동기 작업을 필요로 하는 경우 [std:: future](../../standard-library/future-class.md) 또는 [concurrency:: task](../../parallel/concrt/reference/task-class.md) 를 사용 하는 것이 좋습니다.

*작업* 은 보다 세분화 된 추가 계산으로 분해할 수 있는 계산입니다. *미래* 는 나중에 사용할 수 있도록 값을 계산 하는 비동기 작업입니다.

퓨처를 구현 하기 위해이 항목에서는 클래스를 정의 합니다 `async_future` . `async_future`클래스는 [concurrency:: task_group](reference/task-group-class.md) 클래스와 [concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) 클래스 동시성 런타임의 이러한 구성 요소를 사용 합니다. 클래스는 클래스를 사용 하 여 `async_future` 비동기적으로 `task_group` 값을 계산 하 고 클래스를 사용 하 여 `single_assignment` 계산 결과를 저장 합니다. 클래스의 생성자는 `async_future` 결과를 계산 하는 작업 함수를 사용 하 고, `get` 메서드는 결과를 검색 합니다.

### <a name="to-implement-the-async_future-class"></a>async_future 클래스를 구현하려면

1. `async_future`결과 계산의 형식에 대해 매개 변수가 있는 이라는 템플릿 클래스를 선언 합니다. **`public`** 및 **`private`** 섹션을이 클래스에 추가 합니다.

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. **`private`** 클래스의 섹션에서 `async_future` `task_group` 및 `single_assignment` 데이터 멤버를 선언 합니다.

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. **`public`** 클래스의 섹션에서 `async_future` 생성자를 구현 합니다. 생성자는 결과를 계산 하는 작업 함수에서 매개 변수화 된 템플릿입니다. 생성자는 데이터 멤버에서 work 함수를 비동기적으로 실행 하 `task_group` 고 [concurrency:: send](reference/concurrency-namespace-functions.md#send) 함수를 사용 하 여 결과를 `single_assignment` 데이터 멤버에 씁니다.

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. **`public`** 클래스의 섹션에서 `async_future` 소멸자를 구현 합니다. 소멸자는 태스크가 완료 될 때까지 기다립니다.

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. **`public`** 클래스의 섹션에서 `async_future` 메서드를 구현 `get` 합니다. 이 메서드는 [concurrency:: receive](reference/concurrency-namespace-functions.md#receive) 함수를 사용 하 여 작업 함수의 결과를 검색 합니다.

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 예제에서는 전체 `async_future` 클래스 및 사용 예제를 보여 줍니다. `wmain`함수는 1만 임의의 정수 값을 포함 하는 std::[vector](../../standard-library/vector-class.md) 개체를 만듭니다. 그런 다음 개체를 사용 하 여 `async_future` 개체에 포함 된 가장 작은 값과 가장 큰 값을 찾습니다 `vector` .

### <a name="code"></a>코드

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>주석

이 예제는 다음과 같은 출력을 생성합니다.

```Output
smallest: 0
largest:  9999
average:  4981
```

이 예제에서는 메서드를 사용 하 여 `async_future::get` 계산 결과를 검색 합니다. `async_future::get`메서드는 계산이 아직 활성 상태인 경우 계산이 완료 될 때까지 대기 합니다.

## <a name="robust-programming"></a>강력한 프로그래밍

`async_future`작업 함수에서 throw 된 예외를 처리 하도록 클래스를 확장 하려면 메서드를 수정 하 여 `async_future::get` [concurrency:: task_group:: wait](reference/task-group-class.md#wait) 메서드를 호출 합니다. `task_group::wait`메서드는 작업 함수에 의해 생성 된 모든 예외를 throw 합니다.

다음 예제에서는 클래스의 수정 된 버전을 보여 줍니다 `async_future` . `wmain`함수는 블록을 사용 하 여 **`try`** - **`catch`** 개체의 결과를 인쇄 `async_future` 하거나 작업 함수에 의해 생성 된 예외의 값을 인쇄 합니다.

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

```Output
caught exception: error
```

동시성 런타임의 예외 처리 모델에 대 한 자세한 내용은 [예외 처리](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)를 참조 하세요.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `futures.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

**cl.exe/EHsc. .cpp**

## <a name="see-also"></a>참고 항목

[동시성 런타임 연습](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[예외 처리](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[task_group 클래스](reference/task-group-class.md)<br/>
[single_assignment 클래스](../../parallel/concrt/reference/single-assignment-class.md)
