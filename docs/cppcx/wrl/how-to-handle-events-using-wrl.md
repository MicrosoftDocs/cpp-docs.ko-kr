---
description: '자세한 정보: 방법: WRL를 사용 하 여 이벤트 처리'
title: '방법: WRL을 사용하여 이벤트 처리'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
ms.openlocfilehash: b1be04c1356594e2dc2060d031f35d836ad277bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229186"
---
# <a name="how-to-handle-events-using-wrl"></a>방법: WRL을 사용하여 이벤트 처리

이 문서에서는 Windows 런타임 c + + 템플릿 라이브러리 (WRL)를 사용 하 여 Windows 런타임 개체의 이벤트를 구독 하 고 처리 하는 방법을 보여 줍니다.

해당 구성 요소의 인스턴스를 만들고 속성 값을 검색 하는 보다 기본적인 예제는 [방법: Windows 런타임 구성 요소 활성화 및 사용](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)을 참조 하세요.

## <a name="subscribing-to-and-handling-events"></a>이벤트 구독 및 처리

다음 단계에서는 개체를 시작 하 `ABI::Windows::System::Threading::IDeviceWatcher` 고 이벤트 처리기를 사용 하 여 진행률을 모니터링 합니다. 인터페이스를 사용 하면 장치 `IDeviceWatcher` 를 비동기적으로 열거 하거나 백그라운드에서 장치를 열거 하 고 장치가 추가, 제거 또는 변경 될 때 알림을 받을 수 있습니다. [콜백](callback-function-wrl.md) 함수는이 예제에서 백그라운드 작업의 결과를 처리 하는 이벤트 처리기를 지정할 수 있도록 하기 때문에 중요 한 부분입니다. 전체 예제는 다음과 같습니다.

> [!WARNING]
> 일반적으로 유니버설 Windows 플랫폼 응용 프로그램에서 Windows 런타임 c + + 템플릿 라이브러리를 사용 하지만이 예제에서는 콘솔 앱을 사용 합니다. 와 같은 함수 `wprintf_s` 는 유니버설 Windows 플랫폼 앱에서 사용할 수 없습니다. 유니버설 Windows 플랫폼 앱에서 사용할 수 있는 형식 및 함수에 대 한 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원 되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) 및 [UWP 앱 용 Win32 및 COM](/uwp/win32-and-com/win32-and-com-for-uwp-apps)을 참조 하세요.

1. `#include`필요한 Windows 런타임, Windows 런타임 c + + 템플릿 라이브러리 또는 c + + 표준 라이브러리 헤더를 포함 합니다.

   [!code-cpp[wrl-consume-event#2](../codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]

   `Windows.Devices.Enumeration.h` 장치를 열거 하는 데 필요한 형식을 선언 합니다.

   .cpp 파일의 `using namespace` 지시문을 활용하여 코드를 보다 읽기 쉽게 만드는 것이 좋습니다.

2. 앱에 대 한 지역 변수를 선언 합니다. 이 예제에서는 나중에 이벤트의 구독을 취소할 수 있도록 하는 열거 된 장치 및 등록 토큰 수의 수를 포함 합니다.

   [!code-cpp[wrl-consume-event#7](../codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]

3. Windows 런타임를 초기화 합니다.

   [!code-cpp[wrl-consume-event#3](../codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]

4. 열거 프로세스의 완료를 주 앱에 동기화 하는 [이벤트](event-class-wrl.md) 개체를 만듭니다.

   [!code-cpp[wrl-consume-event#4](../codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]

   > [!NOTE]
   > 이 이벤트는 콘솔 앱의 일부로만 데모용입니다. 이 예제에서는 이벤트를 사용 하 여 앱이 종료 되기 전에 비동기 작업이 완료 되도록 합니다. 대부분의 앱에서 일반적으로 비동기 작업이 완료 될 때까지 기다리지 않습니다.

5. 인터페이스에 대 한 활성화 팩터리를 만듭니다 `IDeviceWatcher` .

   [!code-cpp[wrl-consume-event#5](../codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]

   Windows 런타임는 정규화 된 이름을 사용 하 여 형식을 식별 합니다. `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation`매개 변수는 Windows 런타임에서 제공 하 고 필요한 런타임 클래스 이름을 포함 하는 문자열입니다.

6. `IDeviceWatcher` 개체를 만듭니다.

   [!code-cpp[wrl-consume-event#6](../codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]

7. 함수를 사용 `Callback` 하 여 `Added` , 및 이벤트를 구독 `EnumerationCompleted` `Stopped` 합니다.

   [!code-cpp[wrl-consume-event#8](../codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]

   `Added`이벤트 처리기는 열거 된 장치의 수를 늘립니다. 10 개의 장치를 찾은 후 열거 프로세스를 중지 합니다.

   `Stopped`이벤트 처리기는 이벤트 처리기를 제거 하 고 완료 이벤트를 설정 합니다.

   `EnumerationCompleted`이벤트 처리기가 열거 프로세스를 중지 합니다. 장치를 10 개 미만으로 제공 하는 경우이 이벤트를 처리 합니다.

   > [!TIP]
   > 이 예제에서는 람다 식을 사용 하 여 콜백을 정의 합니다. 함수 개체 (함수), 함수 포인터 또는 [std:: function](../../standard-library/function-class.md) 개체를 사용할 수도 있습니다. 람다 식에 대 한 자세한 내용은 [람다 식](../../cpp/lambda-expressions-in-cpp.md)을 참조 하세요.

8. 열거 프로세스를 시작 합니다.

   [!code-cpp[wrl-consume-event#9](../codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]

9. 열거 프로세스가 완료 될 때까지 기다린 다음 메시지를 인쇄 합니다. 모든 `ComPtr` 및 RAII 개체는 범위를 벗어나면 자동으로 릴리스됩니다.

   [!code-cpp[wrl-consume-event#10](../codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]

다음은 전체 예제입니다.

[!code-cpp[wrl-consume-event#1](../codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]

## <a name="compiling-the-code"></a>코드 컴파일

코드를 컴파일하려면 코드를 복사한 다음 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 후 `wrl-consume-events.cpp` **Visual Studio 명령 프롬프트** 창에서 다음 명령을 실행 합니다.

`cl.exe wrl-consume-events.cpp runtimeobject.lib`

## <a name="see-also"></a>참고 항목

[Windows 런타임 C++ 템플릿 라이브러리(WRL)](windows-runtime-cpp-template-library-wrl.md)
