---
description: '자세한 정보: 연습: 작업 및 XML HTTP 요청을 사용 하 여 연결'
title: '연습: 작업 및 XML HTTP 요청을 사용하여 연결'
ms.date: 04/25/2019
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
ms.openlocfilehash: 88f58639b09c1b996922261c889c4844f1da4963
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167567"
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>연습: 작업 및 XML HTTP 요청을 사용하여 연결

이 예제에서는 [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) 및 [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) 인터페이스를 작업과 함께 사용 하 여 UWP (유니버설 Windows 플랫폼) 앱의 웹 서비스에 HTTP GET 및 POST 요청을 보내는 방법을 보여 줍니다. `IXMLHTTPRequest2`를 작업과 함께 결합하여 다른 작업을 사용하여 구성되는 코드를 작성할 수 있습니다. 예를 들어 일련의 작업 중 일부로 다운로드 작업을 사용할 수 있습니다. 다운로드 작업은 작업이 취소되는 경우에도 응답할 수 있습니다.

> [!TIP]
> C + + REST SDK를 사용 하 여 c + + 앱 또는 데스크톱 c + + 응용 프로그램을 사용 하는 UWP 앱에서 HTTP 요청을 수행할 수도 있습니다. 자세한 내용은 [c + + REST SDK (코드명 "카사블랑카")](https://github.com/Microsoft/cpprestsdk)를 참조 하세요.

태스크에 대 한 자세한 내용은 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)를 참조 하세요. UWP 앱에서 작업을 사용 하는 방법에 대 한 자세한 내용은 [c + +의 비동기 프로그래밍](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) 및 [Uwp 앱 용 c + +로 비동기 작업 만들기](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)를 참조 하세요.

이 문서에서는 먼저 `HttpRequest` 및 해당 지원 클래스를 만드는 방법을 보여 줍니다. 그런 다음 c + + 및 XAML을 사용 하는 UWP 앱에서이 클래스를 사용 하는 방법을 보여 줍니다.

를 사용 `IXMLHTTPRequest2` 하지만 작업을 사용 하지 않는 예제는 빠른 시작 [: XML HTTP 요청을 사용 하 여 연결 (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\))을 참조 하세요.

> [!TIP]
> `IXMLHTTPRequest2` 및 `IXMLHTTPRequest2Callback` 는 UWP 앱에서 사용 하기 위해 권장 되는 인터페이스입니다. 데스크톱 응용 프로그램에서 사용할 수 있도록 이 예제를 조정할 수도 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

UWP 지원은 Visual Studio 2017 이상에서 선택 사항입니다. 설치 하려면 Windows 시작 메뉴에서 Visual Studio 설치 관리자 열고 사용 중인 Visual Studio 버전을 선택 합니다. **수정** 단추를 클릭 하 고 **UWP 개발** 타일이 선택 되어 있는지 확인 합니다. **선택적 구성 요소** 에서 **c + + UWP 도구** 가 선택 되어 있는지 확인 합니다. Visual studio 2017 용 v141 또는 Visual Studio 2019 용 v142를 사용 합니다.

## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>HttpRequest, HttpRequestBuffersCallback 및 HttpRequestStringCallback 클래스 정의

`IXMLHTTPRequest2` 인터페이스를 사용하여 HTTP를 통한 웹 요청을 만드는 경우 서버 응답을 받고 다른 이벤트에 대응하는 `IXMLHTTPRequest2Callback` 인터페이스를 구현합니다. 이 예제에서는 웹 요청을 만들기 위해 `HttpRequest` 클래스를 정의하고, 응답을 처리하기 위해 `HttpRequestBuffersCallback` 및 `HttpRequestStringCallback` 클래스를 정의합니다. `HttpRequestBuffersCallback` 및 `HttpRequestStringCallback` 클래스는 `HttpRequest` 클래스를 지원합니다. 애플리케이션 코드에서 `HttpRequest` 클래스만 사용하여 작업할 수 있습니다.

`GetAsync` 클래스의 `PostAsync` 및 `HttpRequest` 메서드는 각각 HTTP GET 및 POST 작업을 시작할 수 있도록 합니다. 이러한 메서드는 `HttpRequestStringCallback` 클래스를 사용하여 서버 응답을 문자열로 읽습니다. `SendAsync` 및 `ReadAsync` 메서드를 사용하면 큰 콘텐츠를 청크로 스트리밍할 수 있습니다. 이러한 메서드는 각각 작업을 나타내는 [concurrency:: task](../../parallel/concrt/reference/task-class.md) 를 반환 합니다. `GetAsync` 및 `PostAsync` 메서드는 `task<std::wstring>` 부분이 서버의 응답을 나타내는 `wstring` 값을 생성합니다. `SendAsync` 및 `ReadAsync` 메서드는 `task<void>` 값을 생성합니다. 이러한 작업은 보내기 및 읽기 작업이 끝날 때 완료됩니다.

인터페이스는 `IXMLHTTPRequest2` 비동기적으로 동작 하기 때문에이 예제에서는 [concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) 을 사용 하 여 콜백 개체가 완료 된 후 완료 되는 작업을 만들거나 다운로드 작업을 취소 합니다. `HttpRequest` 클래스는 최종 결과를 설정하기 위해 이 작업에서 작업 기반 연속 작업을 만듭니다. `HttpRequest` 클래스는 작업 기반 연속 작업을 사용하여 이전 작업이 오류를 생성하거나 취소되는 경우에도 연속 작업이 실행되도록 합니다. 작업 기반 연속에 대 한 자세한 내용은 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md) 를 참조 하세요.

취소를 지원하기 위해 `HttpRequest`, `HttpRequestBuffersCallback` 및 `HttpRequestStringCallback` 클래스는 취소 토큰을 사용합니다. `HttpRequestBuffersCallback`및 `HttpRequestStringCallback` 클래스는 [concurrency:: cancellation_token:: register_callback](reference/cancellation-token-class.md#register_callback) 메서드를 사용 하 여 작업 완료 이벤트가 취소에 응답할 수 있도록 합니다. 이 취소 콜백은 다운로드를 중단합니다. 취소에 대 한 자세한 내용은 [취소](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)를 참조 하세요.

### <a name="to-define-the-httprequest-class"></a>HttpRequest 클래스를 정의하려면

1. 주 메뉴에서 **파일**  >  **새로 만들기**  >  **프로젝트** 를 선택 합니다.

1. C + + **비어 있는 앱 (유니버설 Windows)** 템플릿을 사용 하 여 빈 XAML 앱 프로젝트를 만듭니다. 이 예에서는 프로젝트 이름을 `UsingIXMLHTTPRequest2`로 지정합니다.

1. HttpRequest.h라는 헤더 파일과 HttpRequest.cpp라는 소스 파일을 프로젝트에 추가합니다.

1. pch.h에서 다음 코드를 추가합니다.

   [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]

1. HttpRequest.h에서 다음 코드를 추가합니다.

   [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]

1. HttpRequest.cpp에서 다음 코드를 추가합니다.

   [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]

## <a name="using-the-httprequest-class-in-a-uwp-app"></a>UWP 앱에서 HttpRequest 클래스 사용

이 섹션에서는 `HttpRequest` UWP 앱에서 클래스를 사용 하는 방법을 보여 줍니다. 응용 프로그램은 URL 리소스를 정의하는 입력 상자, GET 및 POST 작업을 수행하는 단추 명령 및 현재 작업을 취소하는 단추 명령을 제공합니다.

### <a name="to-use-the-httprequest-class"></a>HttpRequest 클래스를 사용하려면

1. MainPage에서 다음과 같이 [StackPanel](/uwp/api/windows.ui.xaml.controls.stackpanel) 요소를 정의 합니다.

   [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]

1. MainPage.xaml.h에서 다음 `#include` 지시문을 추가합니다.

   [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]

1. MainPage .xaml에서 다음 **`private`** 멤버 변수를 클래스에 추가 합니다. `MainPage`

   [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]

1. MainPage .xaml에서 메서드를 선언 합니다. **`private`** `ProcessHttpRequest`

   [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]

1. MainPage에서 다음 문을 추가 합니다. **`using`**

   [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]

1. MainPage.xaml.cpp에서 `GetButton_Click` 클래스의 `PostButton_Click`, `CancelButton_Click` 및 `MainPage` 메서드를 구현합니다.

   [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]

   > [!TIP]
   > 앱에 취소 지원이 필요 하지 않은 경우 [concurrency:: cancellation_token:: none](reference/cancellation-token-class.md#none) 을 `HttpRequest::GetAsync` 및 `HttpRequest::PostAsync` 메서드에 전달 합니다.

1. MainPage.xaml.cpp에서 `MainPage::ProcessHttpRequest` 메서드를 구현합니다.

   [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]

1. 프로젝트 속성의 **링커**, **입력** 에서 및를 지정 `shcore.lib` `msxml6.lib` 합니다.

다음은 실행 중인 응용 프로그램입니다.

![실행 중인 Windows 런타임 앱](../../parallel/concrt/media/concrt_usingixhr2.png "실행 중인 Windows 런타임 앱")

## <a name="next-steps"></a>다음 단계

[동시성 런타임 연습](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

## <a name="see-also"></a>참고 항목

[작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[PPL에서의 취소](cancellation-in-the-ppl.md)<br/>
[C + +의 비동기 프로그래밍](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)<br/>
[UWP 앱 용 c + +로 비동기 작업 만들기](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)<br/>
[빠른 시작: XML HTTP 요청을 사용 하 여 연결 (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\)) 
 [작업 클래스 (동시성 런타임)](../../parallel/concrt/reference/task-class.md)<br/>
[task_completion_event 클래스](../../parallel/concrt/reference/task-completion-event-class.md)
