---
description: '자세한 정보: 연습: User-Interface 스레드에서 작업 제거'
title: '연습: 사용자 인터페이스 스레드에서 작업 제거'
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 816e8446771cda907397f43386c33476cf3665b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340920"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>연습: 사용자 인터페이스 스레드에서 작업 제거

이 문서에서는 동시성 런타임 사용 하 여 Microsoft Foundation Classes (MFC) 응용 프로그램의 UI (사용자 인터페이스) 스레드에서 수행 하는 작업을 작업자 스레드로 이동 하는 방법을 보여 줍니다. 또한이 문서에서는 긴 그리기 작업의 성능을 향상 시키는 방법을 보여 줍니다.

차단 작업 (예: drawing)을 작업자 스레드에 오프 로드 하 여 UI 스레드에서 작업을 제거 하면 응용 프로그램의 응답성이 향상 됩니다. 이 연습에서는 만델브로트 프랙탈을 생성 하는 그리기 루틴을 사용 하 여 긴 차단 작업을 보여 줍니다. 각 픽셀의 계산은 다른 모든 계산과 독립적 이기 때문에 만델브로트 프랙탈을 생성 하는 것도 병렬 처리에 적합 한 후보입니다.

## <a name="prerequisites"></a>사전 요구 사항

이 연습을 시작 하기 전에 다음 항목을 참조 하세요.

- [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)

- [메시지 전달 함수](../../parallel/concrt/message-passing-functions.md)

- [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)

- [PPL에서의 취소](cancellation-in-the-ppl.md)

또한이 연습을 시작 하기 전에 MFC 응용 프로그램 개발 및 GDI +의 기본 사항을 이해 하는 것이 좋습니다. MFC에 대 한 자세한 내용은 [Mfc 데스크톱 응용 프로그램](../../mfc/mfc-desktop-applications.md)을 참조 하세요. GDI +에 대 한 자세한 내용은 [Gdi +](/windows/win32/gdiplus/-gdiplus-gdi-start)를 참조 하세요.

## <a name="sections"></a><a name="top"></a> 섹션이

이 연습에는 다음과 같은 섹션이 있습니다.

- [MFC 응용 프로그램 만들기](#application)

- [만델브로트 응용 프로그램의 일련 버전 구현](#serial)

- [User-Interface 스레드에서 작업 제거](#removing-work)

- [그리기 성능 향상](#performance)

- [취소 지원 추가](#cancellation)

## <a name="creating-the-mfc-application"></a><a name="application"></a> MFC 응용 프로그램 만들기

이 섹션에서는 기본 MFC 응용 프로그램을 만드는 방법을 설명 합니다.

### <a name="to-create-a-visual-c-mfc-application"></a>Visual C++ MFC 응용 프로그램을 만들려면

1. **Mfc 응용 프로그램 마법사** 를 사용 하 여 모든 기본 설정을 사용 하 여 mfc 응용 프로그램을 만듭니다. 사용 중인 Visual Studio 버전에 대 한 마법사를 여는 방법에 대 한 지침은 [연습: 새 MFC 셸 컨트롤 사용](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md) 을 참조 하세요.

1. 프로젝트 이름 (예:)을 입력 한 `Mandelbrot` 다음 **확인** 을 클릭 하 여 **MFC 응용 프로그램 마법사** 를 표시 합니다.

1. **응용 프로그램 종류** 창에서 **단일 문서** 를 선택 합니다. **문서/뷰 아키텍처 지원** 확인란이 선택 취소 되어 있는지 확인 합니다.

1. **마침** 을 클릭 하 여 프로젝트를 만들고 **MFC 응용 프로그램 마법사** 를 닫습니다.

   응용 프로그램을 빌드하고 실행 하 여 성공적으로 만들어졌는지 확인 합니다. 응용 프로그램을 빌드하려면 **빌드** 메뉴에서 **솔루션 빌드** 를 클릭 합니다. 응용 프로그램이 성공적으로 빌드되면 **디버그** 메뉴에서 **디버깅 시작** 을 클릭 하 여 응용 프로그램을 실행 합니다.

## <a name="implementing-the-serial-version-of-the-mandelbrot-application"></a><a name="serial"></a> 만델브로트 응용 프로그램의 일련 버전 구현

이 섹션에서는 만델브로트 프랙탈을 그리는 방법을 설명 합니다. 이 버전은 만델브로트 프랙탈을 GDI + [비트맵](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) 개체에 그린 다음 해당 비트맵의 내용을 클라이언트 창에 복사 합니다.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>만델브로트 응용 프로그램의 일련 버전을 구현 하려면

1. *Pch .h* (Visual Studio 2017 및 이전 버전의 *stdafx.h* )에서 다음 지시문을 추가 합니다. `#include`

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. ChildView. h에서 지시문 뒤에 `pragma` 형식을 정의 합니다. `BitmapPtr` `BitmapPtr`형식을 사용 하면 개체에 대 한 포인터를 `Bitmap` 여러 구성 요소에서 공유할 수 있습니다. `Bitmap`개체는 구성 요소에서 더 이상 참조 되지 않는 경우 삭제 됩니다.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. ChildView. h에서 **`protected`** 클래스의 섹션에 다음 코드를 추가 합니다. `CChildView`

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. ChildView .cpp에서 다음 줄을 주석으로 처리 하거나 제거 합니다.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   디버그 빌드에서이 단계를 수행 하면 응용 프로그램이 `DEBUG_NEW` GDI +와 호환 되지 않는 할당자를 사용할 수 없습니다.

1. ChildView. .cpp에서 **`using`** 네임 스페이스에 지시문을 추가 `Gdiplus` 합니다.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. 클래스의 생성자 및 소멸자에 다음 코드를 추가 `CChildView` 하 여 GDI +를 초기화 하 고 종료 합니다.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. `CChildView::DrawMandelbrot` 메서드를 구현합니다. 이 메서드는 지정 된 개체에 만델브로트 프랙탈을 그립니다 `Bitmap` .

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. `CChildView::OnPaint` 메서드를 구현합니다. 이 메서드는 `CChildView::DrawMandelbrot` 를 호출 하 고 개체의 내용을 `Bitmap` 창에 복사 합니다.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. 응용 프로그램이 빌드 및 실행 되어 성공적으로 업데이트 되었는지 확인 합니다.

다음 그림에서는 만델브로트 응용 프로그램의 결과를 보여 줍니다.

![Mandelbrot 응용 프로그램](../../parallel/concrt/media/mandelbrot.png "Mandelbrot 응용 프로그램")

각 픽셀에 대 한 계산은 계산 비용이 많이 들기 때문에 UI 스레드는 전체 계산이 완료 될 때까지 추가 메시지를 처리할 수 없습니다. 이렇게 하면 응용 프로그램의 응답성이 저하 될 수 있습니다. 그러나 UI 스레드에서 작업을 제거 하 여이 문제를 완화 시킬 수 있습니다.

[[맨 위로](#top)이동]

## <a name="removing-work-from-the-ui-thread"></a><a name="removing-work"></a> UI 스레드에서 작업 제거

이 섹션에서는 만델브로트 응용 프로그램의 UI 스레드에서 그리기 작업을 제거 하는 방법을 보여 줍니다. Ui 스레드에서 작업자 스레드로 그리기 작업을 이동 하면 작업자 스레드가 백그라운드에서 이미지를 생성할 때 UI 스레드가 메시지를 처리할 수 있습니다.

동시성 런타임 작업 [그룹](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [비동기 에이전트](../../parallel/concrt/asynchronous-agents.md)및 [간단한 작업](../../parallel/concrt/task-scheduler-concurrency-runtime.md)을 실행 하는 세 가지 방법을 제공 합니다. 이러한 메커니즘 중 하나를 사용 하 여 UI 스레드에서 작업을 제거할 수 있지만이 예제에서는 작업 그룹이 취소를 지원 하기 때문에 [concurrency:: task_group](reference/task-group-class.md) 개체를 사용 합니다. 이 연습에서는 나중에 취소를 사용 하 여 클라이언트 창의 크기를 조정할 때 수행 되는 작업의 양을 줄이고 창이 소멸 될 때 정리를 수행 합니다.

또한이 예제에서는 [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) 개체를 사용 하 여 UI 스레드 및 작업자 스레드가 서로 통신할 수 있도록 합니다. 작업자 스레드는 이미지를 생성 한 후 개체에 대 한 포인터를 `Bitmap` 개체에 보낸 `unbounded_buffer` 다음 그리기 메시지를 UI 스레드에 게시 합니다. 그러면 UI 스레드가 개체에서 개체를 받아서 `unbounded_buffer` `Bitmap` 클라이언트 창에 그립니다.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>UI 스레드에서 그리기 작업을 제거 하려면

1. *Pch .h* (Visual Studio 2017 및 이전 버전의 *stdafx.h* )에서 다음 지시문을 추가 합니다. `#include`

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. ChildView. h에서 `task_group` `unbounded_buffer` 클래스의 섹션에 및 멤버 변수를 추가 **`protected`** `CChildView` 합니다. `task_group`개체는 그리기를 수행 하는 작업을 포함 하며 `unbounded_buffer` 개체는 완료 된 만델브로트 이미지를 보유 합니다.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. ChildView. .cpp에서 **`using`** 네임 스페이스에 지시문을 추가 `concurrency` 합니다.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. `CChildView::DrawMandelbrot`메서드에서를 호출한 후 `Bitmap::UnlockBits` [concurrency:: send](reference/concurrency-namespace-functions.md#send) 함수를 호출 하 여 `Bitmap` 개체를 UI 스레드에 전달 합니다. 그런 다음, 그리기 메시지를 UI 스레드에 게시 하 고 클라이언트 영역을 무효화 합니다.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. 업데이트 된 `CChildView::OnPaint` 개체를 받고 `Bitmap` 클라이언트 창에 이미지를 그리기 위해 메서드를 업데이트 합니다.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   `CChildView::OnPaint`메서드는 메시지 버퍼에 만델브로트 이미지가 없는 경우이 이미지를 생성 하는 작업을 만듭니다. 메시지 버퍼에는 `Bitmap` 초기 그리기 메시지 등의 경우와 클라이언트 창 앞에서 다른 창이 이동 된 경우와 같은 개체가 포함 되지 않습니다.

1. 응용 프로그램이 빌드 및 실행 되어 성공적으로 업데이트 되었는지 확인 합니다.

배경에서 그리기 작업을 수행 하기 때문에 이제 UI의 응답성이 향상 됩니다.

[[맨 위로](#top)이동]

## <a name="improving-drawing-performance"></a><a name="performance"></a> 그리기 성능 향상

각 픽셀의 계산은 다른 모든 계산과 독립적 이기 때문에 만델브로트 프랙탈 생성은 병렬 처리에 적합 한 후보입니다. 그리기 프로시저를 병렬화 하려면 **`for`** `CChildView::DrawMandelbrot` 다음과 같이 메서드의 외부 루프를 [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 알고리즘에 대 한 호출로 변환 합니다.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

각 bitmap 요소의 계산은 독립적 이므로 비트맵 메모리에 액세스 하는 그리기 작업을 동기화 하지 않아도 됩니다. 이렇게 하면 사용 가능한 프로세서 수가 늘어남에 따라 성능을 확장할 수 있습니다.

[[맨 위로](#top)이동]

## <a name="adding-support-for-cancellation"></a><a name="cancellation"></a> 취소 지원 추가

이 섹션에서는 창 크기 조정을 처리 하는 방법과 창이 소멸 될 때 활성화 된 그리기 작업을 취소 하는 방법을 설명 합니다.

[PPL의 문서 취소](cancellation-in-the-ppl.md) 는 런타임에서 취소가 작동 하는 방식에 대해 설명 합니다. 취소는 협조적입니다. 따라서 즉시 발생 하지 않습니다. 취소 된 작업을 중지 하기 위해 런타임은 작업에서 런타임으로의 후속 호출 중에 내부 예외를 throw 합니다. 이전 섹션에서는 알고리즘을 사용 하 여 `parallel_for` 그리기 작업의 성능을 향상 시키는 방법을 보여 줍니다. 를 호출 하면 `parallel_for` 런타임에서 작업을 중지할 수 있으므로 취소가 작동할 수 있습니다.

### <a name="cancelling-active-tasks"></a>활성 작업 취소

만델브로트 응용 프로그램은 해당 `Bitmap` 차원이 클라이언트 창의 크기와 일치 하는 개체를 만듭니다. 클라이언트 창의 크기를 조정할 때마다 응용 프로그램은 새 창 크기에 대 한 이미지를 생성 하는 추가 백그라운드 작업을 만듭니다. 응용 프로그램에는 이러한 중간 이미지가 필요 하지 않습니다. 최종 창 크기에 대 한 이미지만 필요 합니다. 응용 프로그램에서 이러한 추가 작업을 수행 하지 않도록 하려면 및 메시지에 대 한 메시지 처리기에서 활성 그리기 작업을 취소 한 `WM_SIZE` `WM_SIZING` 다음 창의 크기가 조정 된 후에 그리기 작업을 다시 예약할 수 있습니다.

창의 크기를 조정할 때 활성 그리기 작업을 취소 하기 위해 응용 프로그램은 및 메시지에 대 한 처리기에서 [concurrency:: task_group:: cancel](reference/task-group-class.md#cancel) 메서드를 호출 합니다 `WM_SIZING` `WM_SIZE` . 또한 메시지 처리기는 `WM_SIZE` [concurrency:: task_group:: wait](reference/task-group-class.md#wait) 메서드를 호출 하 여 모든 활성 태스크가 완료 될 때까지 대기한 다음 업데이트 된 창 크기에 대 한 그리기 작업을 다시 예약 합니다.

클라이언트 창이 소멸 되 면 활성 그리기 작업을 취소 하는 것이 좋습니다. 활성 그리기 작업을 취소 하면 클라이언트 창이 소멸 된 후 작업자 스레드가 UI 스레드에 메시지를 게시 하지 않습니다. 응용 프로그램은 메시지에 대 한 처리기에서 활성 그리기 작업을 모두 취소 합니다 `WM_DESTROY` .

### <a name="responding-to-cancellation"></a>취소에 응답

`CChildView::DrawMandelbrot`그리기 작업을 수행 하는 메서드는 취소에 응답 해야 합니다. 런타임에서는 예외 처리를 사용 하 여 작업을 취소 하기 때문에 `CChildView::DrawMandelbrot` 메서드는 모든 리소스가 올바르게 정리 되도록 보장 하기 위해 예외 안전 메커니즘을 사용 해야 합니다. 이 예제에서는 RAII ( *Resource Logis Initialization* ) 패턴을 사용 하 여 작업이 취소 될 때 비트맵 비트의 잠금이 해제 되도록 합니다.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>만델브로트 응용 프로그램에서 취소에 대 한 지원을 추가 하려면

1. ChildView. h의 **`protected`** 클래스 섹션에서 `CChildView` `OnSize` , `OnSizing` 및 메시지 맵 함수에 대 한 선언을 추가 `OnDestroy` 합니다.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. ChildView .cpp에서 `WM_SIZE` , `WM_SIZING` 및 `WM_DESTROY` 메시지에 대 한 처리기를 포함 하도록 메시지 맵을 수정 합니다.

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. `CChildView::OnSizing` 메서드를 구현합니다. 이 메서드는 기존 그리기 작업을 모두 취소 합니다.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. `CChildView::OnSize` 메서드를 구현합니다. 이 메서드는 기존 그리기 작업을 취소 하 고 업데이트 된 클라이언트 창 크기에 대 한 새 그리기 작업을 만듭니다.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. `CChildView::OnDestroy` 메서드를 구현합니다. 이 메서드는 기존 그리기 작업을 모두 취소 합니다.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. ChildView에서 `scope_guard` RAII 패턴을 구현 하는 클래스를 정의 합니다.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. 호출 후에 다음 코드를 `CChildView::DrawMandelbrot` 메서드에 추가 합니다 `Bitmap::LockBits` .

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   이 코드는 개체를 만들어 취소를 처리 `scope_guard` 합니다. 개체가 범위를 벗어나면 비트맵 비트의 잠금이 해제 됩니다.

1. `CChildView::DrawMandelbrot` `scope_guard` 비트맵 비트의 잠금이 해제 된 후 메시지를 UI 스레드로 보내기 전에 메서드 끝을 수정 하 여 개체를 해제 합니다. 이렇게 하면 비트맵 비트의 잠금이 해제 되기 전에 UI 스레드가 업데이트 되지 않습니다.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

1. 응용 프로그램이 빌드 및 실행 되어 성공적으로 업데이트 되었는지 확인 합니다.

창의 크기를 조정할 때 그리기 작업은 최종 창 크기에 대해서만 수행 됩니다. 모든 활성 그리기 작업은 창이 소멸 될 때에도 취소 됩니다.

[[맨 위로](#top)이동]

## <a name="see-also"></a>참고 항목

[동시성 런타임 연습](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[메시지 전달 함수](../../parallel/concrt/message-passing-functions.md)<br/>
[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL에서의 취소](cancellation-in-the-ppl.md)<br/>
[MFC 데스크톱 응용 프로그램](../../mfc/mfc-desktop-applications.md)
