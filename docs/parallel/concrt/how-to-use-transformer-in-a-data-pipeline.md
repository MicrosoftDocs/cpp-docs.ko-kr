---
description: '자세한 정보: 방법: 데이터 파이프라인에서 변환기 사용'
title: '방법: 데이터 파이프라인에서 transformer 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
ms.openlocfilehash: 97b0af16a3ce89b940952117bb8639d281363a23
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205618"
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>방법: 데이터 파이프라인에서 transformer 사용

이 항목에는 데이터 파이프라인에서 [concurrency:: 변환기](../../parallel/concrt/reference/transformer-class.md) 클래스를 사용 하는 방법을 보여 주는 기본 예제가 포함 되어 있습니다. 데이터 파이프라인을 사용 하 여 이미지 처리를 수행 하는 전체 예제는 [연습: Image-Processing 네트워크 만들기](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)를 참조 하세요.

*데이터 파이프라인* 은 동시 프로그래밍의 일반적인 패턴입니다. 데이터 파이프라인은 일련의 단계로 구성 되며, 각 단계는 작업을 수행 하 고 해당 작업의 결과를 다음 단계로 전달 합니다. `transformer`클래스는 입력 값을 받고 해당 값에 대해 작업을 수행한 다음 사용할 다른 구성 요소에 대 한 결과를 생성 하기 때문에 데이터 파이프라인의 핵심 구성 요소입니다.

## <a name="example"></a>예제

이 예제에서는 다음 데이터 파이프라인을 사용 하 여 초기 입력 값이 지정 된 일련의 변환을 수행 합니다.

1. 첫 번째 단계는 해당 입력의 절대값을 계산 합니다.

1. 두 번째 단계는 해당 입력의 제곱근을 계산 합니다.

1. 세 번째 단계는 해당 입력의 제곱을 계산 합니다.

1. 단계는 해당 입력을 부정 합니다.

1. 다섯 번째 단계는 최종 결과를 메시지 버퍼에 기록 합니다.

마지막으로 파이프라인의 결과를 콘솔에 출력 합니다.

[!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

```Output
The result is -42.
```

데이터 파이프라인의 단계에서 형식이 입력 값과 다른 값을 출력 하는 것이 일반적입니다. 이 예제에서 두 번째 단계는 형식의 값을 **`int`** 입력으로 사용 하 고 해당 값 (a)의 제곱근을 **`double`** 출력으로 생성 합니다.

> [!NOTE]
> 이 예제의 데이터 파이프라인은 설명을 위한 것입니다. 각 변환 작업은 거의 작업을 수행 하지 않으므로 메시지 전달을 수행 하는 데 필요한 오버 헤드는 데이터 파이프라인을 사용 하는 경우의 이점 보다 클 수 있습니다.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `data-pipeline.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc data-pipeline**

## <a name="see-also"></a>참고 항목

[비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[연습: Image-Processing 네트워크 만들기](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)
