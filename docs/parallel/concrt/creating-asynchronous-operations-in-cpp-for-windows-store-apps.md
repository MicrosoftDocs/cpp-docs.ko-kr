---
title: C + + UWP 앱 용 비동기 작업 만들기
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: 59630c7702dffc4b606943e174e44fdba6aecfe8
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176954"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>C + + UWP 앱 용 비동기 작업 만들기

이 문서의 작업 클래스를 사용 하 여 Windows 런타임 UWP (유니버설) 앱에서 Windows ThreadPool 기반 비동기 작업을 생성할 때 염두 할 주요 사항 중 일부를 설명 합니다.

비동기 프로그래밍을 사용 하 여 Windows 런타임 앱 모델의 핵심 구성 요소 이므로 앱 사용자 입력에 응답을 유지할 수 있습니다. UI 스레드를 차단하지 않고 장기 실행 작업을 시작할 수 있으며 해당 작업의 결과를 나중에 받을 수 있습니다. 또한 작업을 취소하고 작업이 백그라운드에서 실행될 때 진행률 알림을 받을 수도 있습니다. 문서 [c + +의 비동기 프로그래밍](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) Visual c + + UWP 앱을 만드는 데 사용할 수 있는 비동기 패턴의 개요를 제공 합니다. 해당 문서 모두 사용 하 고 비동기 Windows 런타임 작업의 체인을 만드는 방법에 설명 합니다. 이 섹션에서는 ppltasks.h의 형식을 사용 하 여 다른 Windows 런타임 구성 요소에서 사용할 수 있는 비동기 작업을 생성 하는 방법을 설명 하 고 비동기 작업을 제어 하는 방법을 실행 됩니다. 또한 [비동기 프로그래밍 패턴 및 팁 (c + + 및 XAML을 사용 하는 Windows 스토어 앱) Hilo의](https://msdn.microsoft.com/library/windows/apps/jj160321.aspx) 에 c + + 및 XAML을 사용 하는 Windows 런타임 앱 인 hilo에서 비동기 작업을 구현 하려면 작업 클래스를 사용 하는 방법에 대해 알아봅니다.

> [!NOTE]
>  사용할 수는 [병렬 패턴 라이브러리](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) 및 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md) UWP 앱에서. 그러나 작업 스케줄러 또는 리소스 관리자는 사용할 수 없습니다. 이 문서에서는 데스크톱 앱 아니라 UWP 앱에만 사용할 수 있는 PPL에서 제공 하는 추가 기능을 설명 합니다.

## <a name="key-points"></a>주요 사항

- [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) 를 사용하여 다른 구성 요소(C++ 이외의 언어로 작성될 수도 있음)에서 사용할 수 있는 비동기 작업을 만듭니다.

- [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) 를 사용하여 비동기 작업을 호출하는 구성 요소에 진행률 알림을 보고합니다.

- 취소 토큰을 사용하여 내부 비동기 작업이 취소될 수 있도록 합니다.

- `create_async` 함수의 동작은 이 함수에 전달된 작업 함수의 반환 형식에 따라 달라집니다. 작업( `task<T>` 또는 `task<void>`)을 반환하는 작업 함수는 `create_async`를 호출한 컨텍스트에서 동기적으로 실행됩니다. `T` 또는 `void` 를 반환하는 작업 함수는 임의의 컨텍스트에서 실행됩니다.

- [concurrency::task::then](reference/task-class.md#then) 메서드를 사용하여 차례로 실행되는 작업의 체인을 만들 수 있습니다. UWP 앱에서 작업의 연속에 대 한 기본 컨텍스트는 해당 태스크를 생성 하는 방법에 따라 다릅니다. 비동기 동작을 작업 생성자에 전달하거나 비동기 동작을 반환하는 람다 식을 전달하여 작업을 만든 경우 해당 작업의 모든 연속에 대한 기본 컨텍스트는 현재 컨텍스트입니다. 비동기 동작에서 작업을 생성하지 않은 경우에는 임의의 컨텍스트가 작업의 연속에 기본적으로 사용됩니다. 기본 컨텍스트는 [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) 클래스를 사용하여 재정의할 수 있습니다.

## <a name="in-this-document"></a>이 문서에서 다루는 내용

- [비동기 작업 만들기](#create-async)

- [예: C++ Windows 런타임 구성 요소를 만들기](#example-component)

- [실행 스레드 제어](#exethread)

- [예: c + + 및 XAML을 사용 하 여 Windows 런타임 앱에서 실행 제어](#example-app)

##  <a name="create-async"></a> 비동기 작업 만들기

PPL(병렬 패턴 라이브러리)에서 작업 및 연속 모델을 사용하여 백그라운드 작업과 이전 작업이 완료될 때 실행되는 추가 작업을 정의할 수 있습니다. 이 기능은 [concurrency:: task](../../parallel/concrt/reference/task-class.md) 클래스를 통해 제공됩니다. 이 모델과 `task` 클래스에 대한 자세한 내용은 [Task Parallelism](../../parallel/concrt/task-parallelism-concurrency-runtime.md)를 호출한 컨텍스트에서 동기적으로 실행됩니다.

Windows 런타임에서 특수 한 운영 체제 환경 에서만 실행 되는 UWP 앱을 만드는 데 사용할 수 있는 프로그래밍 인터페이스입니다. 이러한 앱 권한이 부여 된 함수, 데이터 형식 및 장치를 사용 하 고 Microsoft Store 배포 됩니다. Windows 런타임은 표현 합니다 *응용 프로그램 이진 인터페이스* (ABI). ABI는 Windows 런타임 Api를 Visual c + +와 같은 프로그래밍 언어를 사용할 수 있도록 하는 기본 이진 계약입니다.

Windows 런타임을 사용 하 여 다양 한 프로그래밍 언어의 유용한 기능을 사용할 수 있으며 하나의 앱에 결합할 수 있습니다. 예를 들어 JavaScript에서 UI를 만들고 C++ 구성 요소에서 계산이 많은 앱 논리를 수행할 수 있습니다. 이러한 계산이 많은 작업을 백그라운드에서 수행하는 기능은 UI 응답 성능을 유지하는 데 핵심적인 요소입니다. 때문에 `task` 클래스는 c + + 비동기 작업 (c + + 이외의 언어로 작성 될 수 있습니다)는 다른 구성 요소에 전달할 Windows 런타임 인터페이스를 사용 해야 합니다. Windows 런타임 비동기 작업을 나타내는 데 사용할 수 있는 네 가지 인터페이스를 제공 합니다.

[Windows::Foundation::IAsyncAction](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncaction.aspx)<br/>
비동기 동작을 나타냅니다.

[Windows::Foundation::IAsyncActionWithProgress\<TProgress>](https://msdn.microsoft.com/library/windows/apps/br206581.aspx)<br/>
진행률을 보고하는 비동기 동작을 나타냅니다.

[Windows::Foundation::IAsyncOperation\<TResult>](https://msdn.microsoft.com/library/windows/apps/br206598.aspx)<br/>
결과를 반환하는 비동기 작업을 나타냅니다.

[Windows::Foundation::IAsyncOperationWithProgress\<TResult, TProgress>](https://msdn.microsoft.com/library/windows/apps/br206594.aspx)<br/>
결과를 반환하고 진행률을 보고하는 비동기 작업을 나타냅니다.

여기서 *동작(action)* 은 비동기 작업에서 값을 생성하지 않음을 의미하고( `void`를 반환하는 함수와 유사함), *작업(operation)* 은 비동기 작업에서 값을 생성함을 의미합니다. *진행률(progress)* 은 작업에서 진행률 메시지를 호출자에게 보고할 수 있음을 의미합니다. JavaScript, .NET Framework 및 Visual C++에서는 ABI 경계를 넘어 사용할 수 있도록 이러한 인터페이스의 인스턴스를 만드는 방법을 자체적으로 제공합니다. Visual C++의 경우 PPL에서 [concurrency:: create_async](reference/concurrency-namespace-functions.md#create_async) 함수를 제공합니다. 이 함수는 Windows 런타임 비동기 작업 또는 작업의 완료를 나타내는 작업을 만듭니다. 합니다 `create_async` 함수는 작업 함수 (일반적으로 람다 식)를 만들고 내부적으로 `task` 개체 및 해당 네 가지 비동기 Windows 런타임 인터페이스 중 하나에서 작업을 래핑합니다.

> [!NOTE]
>  사용 하 여 `create_async` 다른 언어 또는 다른 Windows 런타임 구성 요소에서 액세스할 수 있는 기능을 만들 있는 경우에 합니다. 작업이 동일한 구성 요소에서 C++ 코드를 통해 생성되고 사용되는 것을 알고 있는 경우에는 `task` 클래스를 직접 사용합니다.

`create_async` 의 반환 형식은 해당 인수의 형식에 따라 결정됩니다. 예를 들어 작업 함수에서 값을 반환하지 않고 진행률을 보고하지 않는 경우 `create_async` 는 `IAsyncAction`을 반환합니다. 작업 함수에서 값을 반환하지 않고 진행률을 보고하는 경우 `create_async` 는 `IAsyncActionWithProgress`를 반환합니다. 진행률을 보고하려면 [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) 개체를 작업 함수에 매개 변수로 제공합니다. 진행률을 보고하는 기능을 사용하면 수행된 작업량과 남아 있는 작업량을 백분율 등으로 보고할 수 있습니다. 또한 결과가 사용 가능해지면 결과도 보고할 수 있습니다.

`IAsyncAction`, `IAsyncActionWithProgress<TProgress>`, `IAsyncOperation<TResult>`및 `IAsyncActionOperationWithProgress<TProgress, TProgress>` 인터페이스는 비동기 작업을 취소하는 데 사용할 수 있는 `Cancel` 메서드를 각기 제공합니다. `task` 클래스는 취소 토큰과 함께 작동합니다. 취소 토큰을 사용하여 작업을 취소하면 런타임에서 해당 토큰을 구독하는 새 작업을 시작하지 않습니다. 이미 활성화된 작업은 취소 토큰을 모니터링하고 가능한 경우 중지할 수 있습니다. 이 메커니즘에 대해서는 [Cancellation in the PPL](cancellation-in-the-ppl.md)문서에 자세히 설명되어 있습니다. Windows 런타임을 사용 하 여 작업 취소를 연결할 수 있습니다`Cancel` 두 가지 방법으로 메서드. 첫째, `create_async` concurrency::cancellation_token [개체를 사용하도록](../../parallel/concrt/reference/cancellation-token-class.md) 에 전달하는 작업 함수를 정의할 수 있습니다. `Cancel` 메서드가 호출되면 이 취소 토큰이 취소되고 일반적인 취소 규칙이 `task` 호출을 지원하는 내부 `create_async` 개체에 적용됩니다. `cancellation_token` 개체를 제공하지 않는 경우 내부 `task` 개체는 암시적으로 이 개체를 정의합니다. 작업 함수에서 취소에 협조적으로 응답해야 하는 경우에는 `cancellation_token` 개체를 정의해야 합니다. 섹션 [예제: c + + 및 XAML을 사용 하 여 Windows 런타임 앱에서 실행 제어](#example-app) C# 및 XAML을 사용자 지정 Windows 런타임 c + +를 사용 하는 유니버설 Windows 플랫폼 (UWP) 앱에서 취소를 수행 하는 방법의 예제를 보여 줍니다. 구성 요소입니다.

> [!WARNING]
>  작업 연속의 체인에서는 취소 토큰이 취소될 때 항상 상태를 정리한 다음 [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) 를 호출해야 합니다. `cancel_current_task`를 호출하지 않고 조기에 반환하는 경우 작업이 취소된 상태가 아니라 완료된 상태로 전환됩니다.

다음 표에는 앱에서 비동기 작업을 정의하는 데 사용할 수 있는 조합이 요약되어 있습니다.

|이 Windows 런타임 인터페이스를 만들려면| `create_async`|암시적 취소 토큰을 사용하기 위해 작업 함수에 전달할 매개 변수 형식|명시적 취소 토큰을 사용하기 위해 작업 함수에 전달할 매개 변수 형식|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|`void` 또는 `task<void>`|(없음)|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|`void` 또는 `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` 또는 `task<T>`|(없음)|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` 또는 `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

`task` 함수에 전달하는 작업 함수에서 `create_async` 개체를 반환하거나 값을 반환할 수 있습니다. 이러한 변형은 각기 다른 동작을 생성합니다. 값을 반환하는 경우 작업 함수는 백그라운드 스레드에서 실행될 수 있도록 `task` 에 래핑됩니다. 또한 내부 `task` 는 암시적 취소 토큰을 사용합니다. 반대로 `task` 개체를 반환하는 경우 작업 함수는 동기적으로 실행됩니다. 따라서 `task` 개체를 반환하는 경우에는 앱이 응답 성능을 유지할 수 있도록 작업 함수에서 시간이 많이 걸리는 모든 작업이 작업으로 실행되어야 합니다. 또한 내부 `task` 는 암시적 취소 토큰을 사용하지 않습니다. 따라서 `cancellation_token` 에서 `task` 개체를 반환할 때 취소에 대한 지원이 필요한 경우 `create_async`개체를 사용하도록 작업 함수를 정의해야 합니다.

다음 예제를 만드는 다양 한 방법을 보여 줍니다는 `IAsyncAction` 다른 Windows 런타임 구성 요소에서 사용할 수 있는 개체입니다.

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

##  <a name="example-component"></a> 예: C++ Windows 런타임 구성 요소를 만들어 C#에서 이를 사용

XAML 및 C#을 사용 하 여 계산 집약적인 작업을 수행 하는 UI와 c + + Windows 런타임 구성 요소를 정의 하는 앱을 고려해 야 합니다. 이 예에서 C++ 구성 요소는 지정된 범위에서 소수인 수를 계산합니다. 네 가지 Windows 런타임 비동기 작업 인터페이스 간의 차이 보여 주기 위해, Visual Studio에서 만들어 시작을 **빈 솔루션** 이름을 지정 하 고 `Primes`입니다. 그런 다음 솔루션에 **Windows 런타임 구성 요소** 프로젝트를 추가하고 이름을 `PrimesLibrary`로 지정합니다. 생성된 C++ 헤더 파일에 다음 코드를 추가합니다(이 예에서는 Class1.h의 이름을 Primes.h로 변경). 각 `public` 메서드는 네 가지 비동기 인터페이스 중 하나를 정의합니다. 값을 반환 하는 메서드는 반환 된 [Windows::Foundation::Collections::IVector\<int >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx) 개체입니다. 진행률을 보고하는 메서드는 완료된 전체 작업의 백분율을 정의하는 `double` 값을 생성합니다.

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
>  규칙에 따라 Windows 런타임에서 비동기 메서드 이름은 일반적으로 "Async"로 끝나야합니다.

생성된 C++ 소스 파일에 다음 코드를 추가합니다(이 예에서는 Class1.cpp의 이름을 Primes.cpp로 변경). `is_prime` 함수는 입력이 소수인지 여부를 확인합니다. 나머지 메서드는 `Primes` 클래스를 구현합니다. `create_async` 를 호출할 때마다 이 함수가 호출된 메서드와 호환되는 서명이 사용됩니다. 예를 들어 `Primes::ComputePrimesAsync` 는 `IAsyncAction`을 반환하기 때문에 `create_async` 에 제공되는 작업 함수는 값을 반환하지 않으며 `progress_reporter` 개체를 매개 변수로 사용하지 않습니다.

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

각 메서드는 먼저 입력된 매개 변수는 음수가 아닌 수 있도록 유효성 검사를 수행 합니다. 입력 값이 음수이면 메서드에서 [Platform::InvalidArgumentException](https://msdn.microsoft.com/library/windows/apps/hh755794.aspx)을 throw합니다. 오류 처리에 대해서는 이 섹션의 뒷부분에서 설명합니다.

UWP 앱에서 이러한 메서드를 사용 하려면 다음을 사용 Visual C# **빈 앱 (XAML)** 템플릿을 Visual Studio 솔루션에 두 번째 프로젝트를 추가 합니다. 이 예에서는 프로젝트 이름을 `Primes`로 지정합니다. 그런 다음 `Primes` 프로젝트에서 `PrimesLibrary` 프로젝트에 대한 참조를 추가합니다.

MainPage.xaml에 다음 코드를 추가합니다. 이 코드에서는 C++ 구성 요소를 호출하고 결과를 표시할 수 있도록 UI를 정의합니다.

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

MainPage.xaml의 `MainPage` 클래스에 다음 코드를 추가합니다. 이 코드에서는 `Primes` 개체와 단추 이벤트 처리기를 정의합니다.

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

이러한 메서드는 `async` 및 `await` 키워드를 사용하여 비동기 작업이 완료된 후 UI를 업데이트합니다. UWP 앱에서 비동기 코딩 하는 방법에 대 한 내용은 [스레딩 및 비동기 프로그래밍](/windows/uwp/threading-async)합니다.

`getPrimesCancellation` 및 `cancelGetPrimes` 메서드는 함께 작동하여 사용자가 작업을 취소할 수 있도록 합니다. 사용자가 선택 하는 경우는 **취소** 단추를 `cancelGetPrimes` 메서드 호출 [IAsyncOperationWithProgress\<TResult, TProgress >:: 취소](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncinfo.cancel.aspx) 작업을 취소 하 합니다. 기본 비동기 작업을 관리 하는 동시성 런타임에서 취소가 완료 되었다고 통신 하기 위해 Windows 런타임에서 내부 예외 형식을 throw 합니다. 취소 모델에 대 한 자세한 내용은 참조 하세요. [취소](../../parallel/concrt/cancellation-in-the-ppl.md)합니다.

> [!IMPORTANT]
>  에 올바르게 보고할 Windows 런타임 작업을 취소 했습니다는 PPL을 사용 하려면이 내부 예외 형식을 catch 하지 않습니다. 즉, 모든 예외도 catch하지 않아야 합니다(`catch (...)`). 모든 catch 해야 하는 경우 예외를 Windows 런타임에서 취소 작업을 완료할 수 있도록 하려면 예외를 다시 throw 합니다.

다음 그림에서는 각 옵션을 선택한 후의 `Primes` 앱을 보여 줍니다.

![Windows 런타임 앱 Primes](../../parallel/concrt/media/concrt_windows_primes.png "Windows 런타임 Primes 앱")

`create_async` 를 사용하여 다른 언어에서 사용할 수 있는 비동기 작업을 만드는 예는 [Bing 지도 여정 최적화 프로그램 샘플에서 C++ 사용](https://msdn.microsoft.com/library/windows/apps/hh699891.aspx) 및 [PPL을 사용하는 C++의 Windows 8 비동기 작업](http://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d)을 참조하세요.

##  <a name="exethread"></a> 실행 스레드 제어

Windows 런타임 COM 스레딩 모델을 사용 합니다. 이 모델에서 개체는 동기화를 처리하는 방식에 따라 서로 다른 아파트에 호스트됩니다. 스레드로부터 안전한 개체는 MTA(다중 스레드 아파트)에서 호스트됩니다. 단일 스레드에서 액세스해야 하는 개체는 STA(단일 스레드 아파트)에서 호스트됩니다.

UI가 있는 앱에서 ASTA(응용 프로그램 STA) 스레드는 창 메시지를 펌프하는 작업을 담당하며 STA에서 호스트된 UI 컨트롤을 업데이트할 수 있는 프로세스의 유일한 스레드입니다. 이에 따라 두 가지 결과가 발생합니다. 첫째, 앱의 응답 성능을 유지하기 위해 CPU를 많이 사용하는 모든 I/O 작업은 ASTA 스레드에서 실행되지 않아야 합니다. 둘째, 백그라운드 스레드에서 제공되는 결과는 UI를 업데이트하기 위해 ASTA에 다시 마샬링되어야 합니다. C + + UWP 앱에서 `MainPage` 모든 다른 XAML 페이지는 ATSA에서 실행 합니다. 따라서 ASTA에서 선언된 작업 연속은 기본적으로 그곳에서 실행되므로 연속 본문에서 직접 컨트롤을 업데이트할 수 있습니다. 그러나 작업을 다른 작업에 중첩하는 경우 중첩된 작업의 모든 연속은 MTA에서 실행됩니다. 따라서 이러한 연속이 실행되는 컨텍스트를 명시적으로 지정할지 여부를 고려해야 합니다.

`IAsyncOperation<TResult>`과 같은 비동기 작업에서 만든 작업은 스레딩 세부 사항을 무시하는 데 도움이 될 수 있는 특수한 의미 체계를 사용합니다. 작업이 백그라운드 스레드에서 실행되거나 스레드를 통해 전혀 지원되지 않을 수 있지만 작업의 연속은 연속 작업을 시작한 아파트(즉, `task::then`을 호출한 아파트)에서 실행되도록 기본적으로 보장됩니다. [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) 클래스를 사용하여 연속의 실행 컨텍스트를 제어할 수 있습니다. `task_continuation_context` 개체를 만들려면 다음과 같은 정적 도우미 메서드를 사용합니다.

- 연속이 백그라운드 스레드에서 실행되도록 지정하려면 [concurrency::task_continuation_context::use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) 를 사용합니다.

- 연속이 [을 호출한 스레드에서 실행되도록 지정하려면](reference/task-continuation-context-class.md#use_current) concurrency::task_continuation_context::use_current `task::then`를 사용합니다.

`task_continuation_context` 개체를 [task:: then](reference/task-class.md#then) 메서드에 전달하여 연속의 실행 컨텍스트를 명시적으로 제어하거나, 작업을 다른 아파트에 전달한 다음 `task::then` 메서드를 호출하여 실행 컨텍스트를 암시적으로 제어할 수 있습니다.

> [!IMPORTANT]
>  기본적으로 해당 STA에서 만드는 연속 STA에서 실행에서 UWP 앱의 주 UI 스레드가 STA에서 실행 되므로 따라서 MTA에서 만드는 연속은 MTA에서 실행됩니다.

다음 섹션에서는 디스크에서 파일을 읽고 해당 파일에서 가장 일반적인 단어를 찾은 다음 UI에 결과를 표시하는 앱을 보여 줍니다. UI를 업데이트하는 최종 작업은 UI 스레드에서 발생합니다.

> [!IMPORTANT]
> 이 동작은 UWP 앱에 특정 합니다. 데스크톱 앱의 경우 연속이 실행되는 위치를 제어하지 않습니다. 대신 스케줄러가 각 연속을 실행할 작업자 스레드를 선택합니다.

> [!IMPORTANT]
> STA에서 실행되는 연속의 본문에서 [concurrency::task::wait](reference/task-class.md#wait) 를 호출하지 마세요. 호출하는 경우 이 메서드가 현재 스레드를 차단하고 앱이 응답하지 않게 만들 수 있기 때문에 런타임에서 [concurrency::invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) 을 throw합니다. 그러나 [concurrency::task::get](reference/task-class.md#get) 메서드를 호출하여 작업 기반 연속에서 선행 작업의 결과를 받을 수 있습니다.

##  <a name="example-app"></a> 예: c + + 및 XAML을 사용 하 여 Windows 런타임 앱에서 실행 제어

디스크에서 파일을 읽고 해당 파일에서 가장 일반적인 단어를 찾은 다음 UI에 결과를 표시하는 C++ XAML 앱을 살펴보겠습니다. 이 앱을 만들려면, Visual Studio에서 만들어 시작을 **비어 있는 앱 (유니버설 Windows)** 프로젝트 이름을 지정 하 고 `CommonWords`입니다. 앱 매니페스트에서 **문서 라이브러리** 접근 권한을 지정하여 앱이 문서 폴더에 액세스할 수 있도록 합니다. 또한 텍스트(.txt) 파일 형식을 앱 매니페스트의 선언 섹션에 추가합니다. 앱 기능 및 선언에 대한 자세한 내용은 [앱 패키지 및 배포](https://msdn.microsoft.com/library/windows/apps/hh464929.aspx)를 참조하세요.

MainPage.xaml에서 `Grid` 요소를 업데이트하여 `ProgressRing` 요소와 `TextBlock` 요소를 포함합니다. `ProgressRing` 은 작업이 진행 중임을 나타내고, `TextBlock` 은 계산의 결과를 보여 줍니다.

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

pch.h에 다음 `#include` 문을 추가합니다.

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

`MainPage` 클래스에 다음 메서드 선언을 추가합니다(MainPage.h).

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

MainPage.cpp에 다음 `using` 문을 추가합니다.

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

MainPage.cpp에서 `MainPage::MakeWordList`, `MainPage::FindCommonWords`및 `MainPage::ShowResults` 메서드를 구현합니다. `MainPage::MakeWordList` 및 `MainPage::FindCommonWords` 는 계산이 많은 작업을 수행합니다. `MainPage::ShowResults` 메서드는 UI에 계산의 결과를 표시합니다.

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

`MainPage` 생성자를 수정하여 Homer의 *The Iliad* 라는 책에 있는 일반적인 단어를 UI에 표시하는 연속 작업의 체인을 만듭니다. 텍스트를 개별 단어로 분할하고 일반적인 단어를 찾는 처음 두 연속 작업은 시간이 걸릴 수 있으므로 백그라운드에서 실행되도록 명시적으로 설정됩니다. UI를 업데이트하는 최종 연속 작업은 연속 컨텍스트를 지정하지 않으므로 아파트 스레딩 규칙을 따릅니다.

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
>  이 예에서는 실행 컨텍스트를 지정하는 방법과 연속의 체인을 구성하는 방법을 보여 줍니다. 앞에서 설명했듯이 기본적으로 비동기 작업에서 만든 작업은 `task::then`을 호출한 아파트에서 연속을 실행합니다. 따라서 이 예에서는 `task_continuation_context::use_arbitrary` 를 사용하여 UI와 관련이 없는 작업이 백그라운드 스레드에서 수행되도록 지정합니다.

다음 그림에서는 `CommonWords` 앱의 결과를 보여 줍니다.

![Windows 런타임 CommonWords 앱](../../parallel/concrt/media/concrt_windows_common_words.png "Windows 런타임 CommonWords 앱")

이 예에서는 `task` 를 지원하는 `create_async` 개체가 암시적 취소 토큰을 사용하기 때문에 취소를 지원할 수 있습니다. 작업이 협조적으로 취소에 응답해야 하는 경우 `cancellation_token` 개체를 사용하도록 작업 함수를 정의합니다. PPL에서의 취소에 대한 자세한 내용은 [Cancellation in the PPL](cancellation-in-the-ppl.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[동시성 런타임](../../parallel/concrt/concurrency-runtime.md)
