---
title: C++ AMP(C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: 516b69a0371ceb9365e79d5465879711289076c0
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404862"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP(C++ Accelerated Massive Parallelism)

C++ AMP (C++ Accelerated Massive Parallelism)는 개별 그래픽 카드의 GPU (그래픽 처리 장치)로 일반적으로 존재 하는 데이터 병렬 하드웨어를 활용 하 여 c + + 코드의 실행 속도를 가속화 합니다. C++ AMP 프로그래밍 모델에는 다차원 배열, 인덱싱, 메모리 전송, 바둑판식 배열에 대 한 지원이 포함 됩니다. 또한 수학 함수 라이브러리를 포함 합니다. C++ AMP 언어 확장을 사용 하 여 CPU에서 GPU로 데이터를 이동 하는 방법을 제어할 수 있습니다.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[C++ AMP 개요](../../parallel/amp/cpp-amp-overview.md)|C++ AMP 및 수학 라이브러리의 주요 기능에 대해 설명 합니다.|
|[람다, 함수 개체 및 제한 함수 사용](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|[Parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) 메서드에 대 한 호출에서 람다 식, 함수 개체 및 제한 된 함수를 사용 하는 방법을 설명 합니다.|
|[타일 사용](../../parallel/amp/using-tiles.md)|타일을 사용 하 여 C++ AMP 코드를 가속화 하는 방법을 설명 합니다.|
|[Accelerator 및 accelerator_view 개체 사용](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|액셀러레이터 키를 사용 하 여 GPU에서 코드의 실행을 사용자 지정 하는 방법을 설명 합니다.|
|[UWP 앱에서 C++ AMP 사용](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Windows 런타임 형식을 사용 하는 UWP (유니버설 Windows 플랫폼) 앱에서 C++ AMP를 사용 하는 방법을 설명 합니다.|
|[그래픽(C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|C++ AMP 그래픽 라이브러리를 사용 하는 방법을 설명 합니다.|
|[연습: 행렬 곱하기](../../parallel/amp/walkthrough-matrix-multiplication.md)|C++ AMP 코드와 바둑판식 배열을 사용 하 여 행렬 곱셈을 보여 줍니다.|
|[연습: C++ AMP 애플리케이션 디버깅](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|병렬 감소를 사용 하 여 많은 정수 배열을 합산 하는 응용 프로그램을 만들고 디버그 하는 방법을 설명 합니다.|

## <a name="reference"></a>참고

[참조(C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static 키워드](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>기타 리소스

[네이티브 코드 블로그의 병렬 프로그래밍](https://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[다운로드를 위한 C++ AMP 샘플 프로젝트](https://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[동시성 시각화 도우미를 사용 하 여 C++ AMP 코드 분석](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)
