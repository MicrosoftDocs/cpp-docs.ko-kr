---
description: '자세한 정보: 방법: WRL를 사용 하 여 비동기 작업 완료'
title: '방법: WRL을 사용하여 비동기 작업 완료'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: f8c929d737f113d995b5d171896517b3d94a6aa4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124594"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>방법: WRL을 사용하여 비동기 작업 완료

이 문서에서는 Windows 런타임 c + + 템플릿 라이브러리 (WRL)를 사용 하 여 비동기 작업을 시작 하 고 작업이 완료 되 면 작업을 수행 하는 방법을 보여 줍니다.

이 문서에서는 두 가지 예를 보여 줍니다. 첫 번째 예제에서는 비동기 타이머를 시작 하 고 타이머가 만료 될 때까지 기다립니다. 이 예제에서는 타이머 개체를 만들 때 비동기 작업을 지정 합니다. 두 번째 예제에서는 백그라운드 작업자 스레드를 실행 합니다. 이 예제에서는 인터페이스를 반환 하는 Windows 런타임 메서드를 사용 하는 방법을 보여 줍니다 `IAsyncInfo` . [콜백](callback-function-wrl.md) 함수는 비동기 작업의 결과를 처리 하는 이벤트 처리기를 지정할 수 있도록 하기 때문에 두 예제의 중요 한 부분입니다.

구성 요소의 인스턴스를 만들고 속성 값을 검색 하는 보다 기본적인 예제는 [방법: Windows 런타임 구성 요소 활성화 및 사용](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)을 참조 하세요.

> [!TIP]
> 이러한 예제는 람다 식을 사용 하 여 콜백을 정의 합니다. 함수 개체 (함수), 함수 포인터 또는 [std:: function](../../standard-library/function-class.md) 개체를 사용할 수도 있습니다. C + + 람다 식에 대 한 자세한 내용은 [람다 식](../../cpp/lambda-expressions-in-cpp.md)을 참조 하세요.

## <a name="example-working-with-a-timer"></a>예: 타이머 사용

다음 단계는 비동기 타이머를 시작 하 고 타이머가 만료 될 때까지 기다립니다. 전체 예제는 다음과 같습니다.

> [!WARNING]
> 일반적으로 UWP (유니버설 Windows 플랫폼) 앱에서 Windows 런타임 c + + 템플릿 라이브러리를 사용 하지만이 예제에서는 콘솔 앱을 사용 하 여 설명 합니다. 와 같은 함수 `wprintf_s` 는 UWP 앱에서 사용할 수 없습니다. UWP 앱에서 사용할 수 있는 형식 및 함수에 대 한 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원 되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) 및 [Uwp 앱 용 Win32 및 COM](/uwp/win32-and-com/win32-and-com-for-uwp-apps)을 참조 하세요.

1. `#include`필요한 Windows 런타임, Windows 런타임 c + + 템플릿 라이브러리 또는 c + + 표준 라이브러리 헤더를 포함 합니다.

   [!code-cpp[wrl-consume-async#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` 비동기 타이머를 사용 하는 데 필요한 형식을 선언 합니다.

   .cpp 파일의 `using namespace` 지시문을 활용하여 코드를 보다 읽기 쉽게 만드는 것이 좋습니다.

2. Windows 런타임를 초기화 합니다.

   [!code-cpp[wrl-consume-async#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. 인터페이스에 대 한 활성화 팩터리를 만듭니다 `ABI::Windows::System::Threading::IThreadPoolTimer` .

   [!code-cpp[wrl-consume-async#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   Windows 런타임는 정규화 된 이름을 사용 하 여 형식을 식별 합니다. `RuntimeClass_Windows_System_Threading_ThreadPoolTimer`매개 변수는 Windows 런타임에서 제공 하 고 필요한 런타임 클래스 이름을 포함 하는 문자열입니다.

4. 타이머 콜백을 주 앱에 동기화 하는 [이벤트](event-class-wrl.md) 개체를 만듭니다.

   [!code-cpp[wrl-consume-async#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > 이 이벤트는 콘솔 앱의 일부로만 데모용입니다. 이 예제에서는 이벤트를 사용 하 여 앱이 종료 되기 전에 비동기 작업이 완료 되도록 합니다. 대부분의 앱에서 일반적으로 비동기 작업이 완료 될 때까지 기다리지 않습니다.

5. `IThreadPoolTimer`2 초 후에 만료 되는 개체를 만듭니다. 함수를 사용 `Callback` 하 여 이벤트 처리기 ( `ABI::Windows::System::Threading::ITimerElapsedHandler` 개체)를 만듭니다.

   [!code-cpp[wrl-consume-async#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. 콘솔에 메시지를 출력 하 고 타이머 콜백이 완료 될 때까지 기다립니다. 모든 `ComPtr` 및 RAII 개체는 범위를 벗어나면 자동으로 릴리스됩니다.

   [!code-cpp[wrl-consume-async#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

다음은 전체 예제입니다.

[!code-cpp[wrl-consume-async#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>코드 컴파일

코드를 컴파일하려면 코드를 복사한 다음 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 후 `wrl-consume-async.cpp` Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>예: 백그라운드 스레드 작업

다음 단계는 작업자 스레드를 시작 하 고 해당 스레드에서 수행 하는 작업을 정의 합니다. 전체 예제는 다음과 같습니다.

> [!TIP]
> 이 예제에서는 인터페이스를 사용 하는 방법을 보여 줍니다 `ABI::Windows::Foundation::IAsyncAction` . ,, 및를 구현 하는 모든 인터페이스에이 패턴을 적용할 수 있습니다 `IAsyncInfo` `IAsyncAction` `IAsyncActionWithProgress` `IAsyncOperation` `IAsyncOperationWithProgress` .

1. `#include`필요한 Windows 런타임, Windows 런타임 c + + 템플릿 라이브러리 또는 c + + 표준 라이브러리 헤더를 포함 합니다.

   [!code-cpp[wrl-consume-asyncOp#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   Tem를 Windows.Sys합니다. 스레딩은 작업자 스레드를 사용 하는 데 필요한 형식을 선언 합니다.

   `using namespace`.Cpp 파일에서 지시문을 사용 하 여 코드를 보다 읽기 쉽게 만드는 것이 좋습니다.

2. Windows 런타임를 초기화 합니다.

   [!code-cpp[wrl-consume-asyncOp#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. 인터페이스에 대 한 활성화 팩터리를 만듭니다 `ABI::Windows::System::Threading::IThreadPoolStatics` .

   [!code-cpp[wrl-consume-asyncOp#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. 작업자 스레드의 완료를 주 앱에 동기화 하는 [이벤트](event-class-wrl.md) 개체를 만듭니다.

   [!code-cpp[wrl-consume-asyncOp#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > 이 이벤트는 콘솔 앱의 일부로만 데모용입니다. 이 예제에서는 이벤트를 사용 하 여 앱이 종료 되기 전에 비동기 작업이 완료 되도록 합니다. 대부분의 앱에서 일반적으로 비동기 작업이 완료 될 때까지 기다리지 않습니다.

5. 메서드를 호출 `IThreadPoolStatics::RunAsync` 하 여 작업자 스레드를 만듭니다. 함수를 사용 `Callback` 하 여 작업을 정의 합니다.

   [!code-cpp[wrl-consume-asyncOp#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   `IsPrime`함수는 다음의 전체 예제에 정의 되어 있습니다.

6. 콘솔에 메시지를 출력 하 고 스레드가 완료 될 때까지 기다립니다. 모든 `ComPtr` 및 RAII 개체는 범위를 벗어나면 자동으로 릴리스됩니다.

   [!code-cpp[wrl-consume-asyncOp#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

다음은 전체 예제입니다.

[!code-cpp[wrl-consume-asyncOp#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>코드 컴파일

코드를 컴파일하려면 코드를 복사한 다음 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 후 `wrl-consume-asyncOp.cpp` **Visual Studio 명령 프롬프트** 창에서 다음 명령을 실행 합니다.

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>참고 항목

[Windows 런타임 C++ 템플릿 라이브러리(WRL)](windows-runtime-cpp-template-library-wrl.md)
