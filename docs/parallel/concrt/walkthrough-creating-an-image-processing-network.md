---
description: '자세한 정보: 연습: Image-Processing 네트워크 만들기'
title: '연습: 이미지 처리 네트워크 만들기'
ms.date: 04/25/2019
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
ms.openlocfilehash: 1cdd94d6cad6ee76c02b7eb2cf8b4ca38a53fa96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169309"
---
# <a name="walkthrough-creating-an-image-processing-network"></a>연습: 이미지 처리 네트워크 만들기

이 문서에서는 이미지 처리를 수행 하는 비동기 메시지 블록의 네트워크를 만드는 방법을 보여 줍니다.

네트워크는 특성을 기반으로 이미지에서 수행할 작업을 결정 합니다. 이 예제에서는 *데이터 흐름* 모델을 사용 하 여 네트워크를 통해 이미지를 라우팅합니다. 데이터 흐름 모델에서는, 프로그램의 개별 구성 요소가 메시지를 전달하여 서로 통신합니다. 구성 요소가 메시지를 받으면 일부 작업을 수행한 다음 해당 작업의 결과를 다른 구성 요소에 전달할 수 있습니다. 응용 프로그램에서 제어 구조 (예: 조건문, 루프 등)를 사용 하 여 프로그램의 작업 순서를 제어 하는 *제어 흐름* 모델과 비교해 보십시오.

데이터 흐름을 기반으로 하는 네트워크는 작업 *파이프라인* 을 만듭니다. 파이프라인의 각 단계는 전체 작업의 일부를 동시에 수행 합니다. 이는 자동차 제조 조립 라인에 비유될 수 있습니다. 각 차량이 어셈블리 라인을 통과 하면 한 스테이션은 프레임을 조립 하 고 다른 스테이션은 엔진을 설치 합니다. 여러 차량의 동시 어셈블을 가능 하 게 하 여 어셈블리 선은 한 번에 하나씩 전체 차량을 어셈블하는 것 보다 더 나은 처리량을 제공 합니다.

## <a name="prerequisites"></a>사전 요구 사항

이 연습을 시작 하기 전에 다음 문서를 읽어 보세요.

- [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)

- [방법: 메시지 블록 필터 사용](../../parallel/concrt/how-to-use-a-message-block-filter.md)

- [연습: 데이터 흐름 에이전트 만들기](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)

또한이 연습을 시작 하기 전에 GDI +의 기본 사항을 이해 하는 것이 좋습니다.

## <a name="sections"></a><a name="top"></a> 섹션이

이 연습에는 다음과 같은 섹션이 있습니다.

- [이미지 처리 기능 정의](#functionality)

- [이미지 처리 네트워크 만들기](#network)

- [전체 예제](#complete)

## <a name="defining-image-processing-functionality"></a><a name="functionality"></a> 이미지 처리 기능 정의

이 섹션에서는 이미지 처리 네트워크에서 디스크에서 읽은 이미지 작업을 수행 하는 데 사용 하는 지원 기능을 보여 줍니다.

다음 함수 및는 `GetRGB` `MakeColor` 각각 지정 된 색의 개별 구성 요소를 추출 하 고 결합 합니다.

[!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]

다음 함수는 `ProcessImage` 지정 된 [std:: function](../../standard-library/function-class.md) 개체를 호출 하 여 gdi + [비트맵](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) 개체의 각 픽셀에 대 한 색 값을 변환 합니다. `ProcessImage`함수는 [동시성::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 알고리즘을 사용 하 여 비트맵의 각 행을 병렬로 처리 합니다.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]

,,, 및 함수는 `Grayscale` `Sepiatone` 함수를 `ColorMask` `Darken` 호출 하 여 `ProcessImage` 개체의 각 픽셀에 대 한 색 값을 변환 합니다 `Bitmap` . 이러한 각 함수는 람다 식을 사용 하 여 한 픽셀의 색 변환을 정의 합니다.

[!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]

다음 함수는 `GetColorDominance` 도 함수를 호출 합니다 `ProcessImage` . 그러나이 함수는 각 색의 값을 변경 하는 대신 [concurrency:: 결합할](../../parallel/concrt/reference/combinable-class.md) 수 있는 개체를 사용 하 여 빨간색, 녹색 또는 파랑 색 구성 요소가 이미지를 지배 하는지 여부를 계산 합니다.

[!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]

다음 함수는 `GetEncoderClsid` 인코더의 지정 된 MIME 형식에 대 한 클래스 식별자를 검색 합니다. 응용 프로그램은이 함수를 사용 하 여 비트맵의 인코더를 검색 합니다.

[!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]

[[맨 위로](#top)이동]

## <a name="creating-the-image-processing-network"></a><a name="network"></a> 이미지 처리 네트워크 만들기

이 섹션에서는 지정 된 디렉터리의 모든 JPEG (.jpg) 이미지에서 이미지 처리를 수행 하는 비동기 메시지 블록의 네트워크를 만드는 방법을 설명 합니다. 네트워크는 다음과 같은 이미지 처리 작업을 수행 합니다.

1. Tom에서 작성 한 모든 이미지의 경우 회색조로 변환 합니다.

1. 기준 색으로 빨강으로 구성 된 이미지의 경우 녹색 및 파랑 구성 요소를 제거한 후 어둡게 합니다.

1. 다른 이미지의 경우 세피아 toning을 적용 합니다.

네트워크는 다음 조건 중 하 나와 일치 하는 첫 번째 이미지 처리 작업만 적용 합니다. 예를 들어, 이미지가 Tom에 의해 작성 되 고 기준 색으로 빨강으로 되어 있는 경우에는 이미지만 회색조로 변환 됩니다.

네트워크는 각 이미지 처리 작업을 수행한 후 이미지를 비트맵 (.bmp) 파일로 디스크에 저장 합니다.

다음 단계에서는이 이미지 처리 네트워크를 구현 하는 함수를 만들고 해당 네트워크를 지정 된 디렉터리의 모든 JPEG 이미지에 적용 하는 방법을 보여 줍니다.

#### <a name="to-create-the-image-processing-network"></a>이미지 처리 네트워크를 만들려면

1. `ProcessImages`디스크의 디렉터리 이름을 사용 하는 함수를 만듭니다.

   [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]

1. 함수에서 `ProcessImages` 변수를 만듭니다 `countdown_event` . `countdown_event`클래스는이 연습의 뒷부분에 나와 있습니다.

   [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]

1. 개체를 원래 파일 이름과 연결 하는 [std:: map](../../standard-library/map-class.md) 개체를 만듭니다 `Bitmap` .

   [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]

1. 다음 코드를 추가 하 여 이미지 처리 네트워크의 멤버를 정의 합니다.

   [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]

1. 네트워크를 연결 하는 다음 코드를 추가 합니다.

   [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]

1. 다음 코드를 추가 하 여 디렉터리에 있는 각 JPEG 파일의 전체 경로를 네트워크 헤드에 보냅니다.

   [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]

1. 변수가 0에 도달할 때까지 기다립니다 `countdown_event` .

   [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]

다음 표에서는 네트워크의 멤버를 설명합니다.

|멤버|설명|
|------------|-----------------|
|`load_bitmap`|디스크 [](../../parallel/concrt/reference/transformer-class.md) 에서 개체를 로드 하 `Bitmap` 고 개체에 항목을 추가 하 여 `map` 이미지를 원래 파일 이름과 연결 하는 concurrency:: 변환기 개체입니다.|
|`loaded_bitmaps`|로드 된 이미지를 이미지 처리 필터로 보내는 [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) 개체입니다.|
|`grayscale`|`transformer`Tom에 의해 작성 된 이미지를 회색조로 변환 하는 개체입니다. 이미지의 메타 데이터를 사용 하 여 해당 작성자를 확인 합니다.|
|`colormask`|`transformer`색이 빨강 인 이미지에서 녹색 및 파랑 색 구성 요소를 제거 하는 개체입니다.|
|`darken`|`transformer`기준 색으로 빨강을 포함 하는 이미지를 어둡게 하는 개체입니다.|
|`sepiatone`|`transformer`Tom이 작성 하지 않은 이미지에 세피아 toning를 적용 하는 개체입니다.|
|`save_bitmap`|`transformer`처리 된를 `image` 디스크에 비트맵으로 저장 하는 개체입니다. `save_bitmap` 개체에서 원래 파일 이름을 검색 `map` 하 고 파일 이름 확장명을 .bmp로 변경 합니다.|
|`delete_bitmap`|`transformer`이미지에 대 한 메모리를 해제 하는 개체입니다.|
|`decrement`|네트워크의 터미널 노드 역할을 하는 [concurrency:: call](../../parallel/concrt/reference/call-class.md) 개체입니다. `countdown_event`이미지가 처리 되었음을 주 응용 프로그램에 알리기 위해 개체를 감소 시킵니다.|

`loaded_bitmaps`메시지 버퍼는 개체 이기 때문에 `unbounded_buffer` `Bitmap` 여러 수신자에 게 개체를 제공 하기 때문에 중요 합니다. 대상 블록이 개체를 수락 하는 경우 개체는 해당 개체를 `Bitmap` `unbounded_buffer` `Bitmap` 다른 대상에 제공 하지 않습니다. 따라서 개체를 개체에 연결 하는 순서는 `unbounded_buffer` 중요 합니다. `grayscale`, `colormask` 및 `sepiatone` 메시지 블록은 각각 필터를 사용 하 여 특정 개체만 수락 `Bitmap` 합니다. 메시지 버퍼는 `decrement` `loaded_bitmaps` `Bitmap` 다른 메시지 버퍼에서 거부 된 모든 개체를 허용 하므로 메시지 버퍼의 중요 한 대상입니다. `unbounded_buffer`메시지를 순서 대로 전파 하려면 개체가 필요 합니다. 따라서 개체는 `unbounded_buffer` 새 대상 블록이 연결 될 때까지 차단 되 고, 해당 메시지를 수락 하는 현재 대상 블록이 없으면 메시지를 수락 합니다.

응용 프로그램에서 메시지를 처리 하는 메시지 블록이 한 번만 메시지를 수락 하는 것이 아니라 여러 메시지 블록에서 메시지를 처리 해야 하는 경우와 같은 다른 메시지 블록 형식을 사용할 수 있습니다 `overwrite_buffer` . `overwrite_buffer`클래스는 한 번에 하나의 메시지를 보유 하지만 해당 메시지를 각 대상에 전파 합니다.

다음 그림에서는 이미지 처리 네트워크를 보여줍니다.

![이미지 처리 네트워크](../../parallel/concrt/media/concrt_imageproc.png "이미지 처리 네트워크")

`countdown_event`이 예제의 개체를 사용 하면 이미지 처리 네트워크에서 모든 이미지가 처리 될 때 주 응용 프로그램에 알릴 수 있습니다. `countdown_event`클래스는 [concurrency:: event](../../parallel/concrt/reference/event-class.md) 개체를 사용 하 여 카운터 값이 0에 도달할 때 신호를 전달 합니다. 주 응용 프로그램은 네트워크에 파일 이름을 보낼 때마다 카운터를 증가 시킵니다. 네트워크의 터미널 노드는 각 이미지가 처리 된 후 카운터를 감소 시킵니다. 주 응용 프로그램은 지정 된 디렉터리를 트래버스하 고 나면 `countdown_event` 개체가 카운터가 0에 도달 했음을 알리기 위해 대기 합니다.

다음 예제에서는 클래스를 보여 줍니다 `countdown_event` .

[!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]

[[맨 위로](#top)이동]

## <a name="the-complete-example"></a><a name="complete"></a> 전체 예제

다음 코드에서는 전체 예제를 보여 줍니다. `wmain`함수는 GDI + 라이브러리를 관리 하 고 `ProcessImages` 함수를 호출 하 여 디렉터리에 있는 JPEG 파일을 처리 합니다 `Sample Pictures` .

[!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]

다음 그림에서는 샘플 출력을 보여 줍니다. 각 원본 이미지는 해당 하는 수정 된 이미지 위에 있습니다.

![예제의 샘플 출력](../../parallel/concrt/media/concrt_imageout.png "예제의 샘플 출력")

`Lighthouse` 는 Tom Alphin에서 작성 되므로 회색조로 변환 됩니다. `Chrysanthemum`, `Desert` , `Koala` 및은 `Tulips` 기준 색으로 빨강을 가지 므로 파란색 및 녹색 색 구성 요소가 제거 되 고 어두운입니다. `Hydrangeas`, `Jellyfish` 및는 `Penguins` 기본 조건과 일치 하므로 세피아 toned입니다.

[[맨 위로](#top)이동]

### <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `image-processing-network.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

**cl.exe/DUNICODE/EHsc image-processing-network/link gdiplus.dll**

## <a name="see-also"></a>참고 항목

[동시성 런타임 연습](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
