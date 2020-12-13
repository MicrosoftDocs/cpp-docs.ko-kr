---
description: '자세한 정보: 대리자 (c + +/CX)'
title: 대리자(C++/CX)
ms.date: 01/22/2017
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
ms.openlocfilehash: 3d62b48d76319d79707330e874e6ceddcc22284e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342012"
---
# <a name="delegates-ccx"></a>대리자(C++/CX)

**`delegate`** 키워드는 표준 c + +에서 함수 개체에 해당 하는 Windows 런타임 참조 형식을 선언 하는 데 사용 됩니다. 대리자 선언은 함수 서명과 유사하며, 래핑된 함수에 있어야 하는 반환 형식과 매개 변수 형식을 지정합니다. 다음은 사용자 정의 대리자 선언입니다.

```cpp
public delegate void PrimeFoundHandler(int result);
```

대리자는 대부분 이벤트와 함께 사용됩니다. 이벤트는 클래스에 인터페이스 형식을 포함할 수 있는 것과 매우 유사한 방식으로 대리자 형식을 포함합니다. 대리자는 이벤트 처리기를 많이 수행하는 계약을 나타냅니다. 이전에 정의된 대리자를 형식으로 갖는 이벤트 클래스 멤버는 다음과 같습니다.

```cpp
event PrimeFoundHandler^ primeFoundEvent;
```

Windows 런타임 응용 프로그램 이진 인터페이스를 통해 클라이언트에 노출 될 대리자를 선언할 때 [Windows:: Foundation:: TypedEventHandler \<TSender, TResult> ](/uwp/api/windows.foundation.typedeventhandler-2)를 사용 합니다. 이 대리자에는 Javascript 클라이언트에서 대리자를 사용할 수 있게 하는 프록시 및 스텁 이진 파일이 미리 정의되어 있습니다.

## <a name="consuming-delegates"></a>대리자 사용

유니버설 Windows 플랫폼 앱을 만들 때 Windows 런타임 클래스가 노출 하는 이벤트의 형식으로 대리자를 사용 하는 경우가 많습니다. 이벤트를 구독하려면 대리자 시그니처와 일치하는 함수(또는 람다)를 지정하여 대리자 형식의 인스턴스를 만듭니다. 그런 다음 `+=` 연산자를 사용하여 클래스의 이벤트 멤버에 대리자 개체를 전달합니다. 이를 이벤트 구독이라고 합니다. 클래스 인스턴스가 이벤트를 "발생"시키면 개체 또는 다른 개체가 추가한 다른 모든 처리기와 함께 함수가 호출됩니다.

> [!TIP]
> 이벤트 처리기를 만들 때 Visual Studio에서는 많은 작업을 수행합니다. 예를 들어 XAML 태그에서 이벤트 처리기를 지정하면 도구 설명이 나타납니다. 도구 설명을 선택하는 경우 Visual Studio에서는 자동으로 이벤트 처리기 메서드를 만들어 게시 클래스에 대한 이벤트와 연결합니다.

다음 예제에서는 기본 패턴을 보여 줍니다. `Windows::Foundation::TypedEventHandler` 는 대리자 형식입니다. 처리기 함수는 명명된 함수를 사용하여 만들어집니다.

app.h에서:

[!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]

app.cpp에서:

[!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]

> [!WARNING]
> 일반적으로 이벤트 처리기의 경우 순환 참조를 방지하기 위해 크게 주의하지 않는 한 람다 대신 명명된 함수를 사용하는 것이 좋습니다. 명명된 함수는 약한 참조로 "this" 포인터를 캡처하지만 람다는 강력한 참조로 캡처하고 순환 참조를 만듭니다. 자세한 내용은 [약한 참조 및 순환 중단](../cppcx/weak-references-and-breaking-cycles-c-cx.md)을 참조 하세요.

규칙에 따라 Windows 런타임에서 정의 된 이벤트 처리기 대리자 이름에는 * EventHandler (예: RoutedEventHandler, SizeChangedEventHandler 또는 Suspendingeventhandler)) 형식이 있습니다. 또한 규칙에 따라 이벤트 처리기 대리자는 매개 변수 2개를 사용하고 void를 반환합니다. 형식 매개 변수가 없는 대리자에서 첫 번째 매개 변수는 [Platform::Object^](../cppcx/platform-object-class.md)형식이며 이벤트를 발생시킨 개체인 전송자에 대한 참조를 보유합니다. 이벤트 처리기 메서드에서 인수를 사용하기 전에 원래 형식으로 다시 캐스팅해야 합니다. 형식 매개 변수가 있는 이벤트 처리기 대리자에서 첫 번째 형식 매개 변수는 전송자의 형식을 지정하고, 두 번째 매개 변수는 이벤트에 대한 정보를 보유하는 ref 클래스에 대한 핸들입니다. 규칙에 따라이 클래스는 EventArgs 라는 이름으로 지정 됩니다 \* . 예를 들어 RoutedEventHandler 대리자에는 RoutedEventArgs^ 형식의 두 번째 매개 변수가 있고, DragEventHander에는 DragEventArgs^ 형식의 두 번째 매개 변수가 있습니다.

규칙에 따라 비동기 작업이 완료될 때 실행되는 코드를 래핑하는 대리자의 이름은 *CompletedHandler로 지정됩니다. 이러한 대리자는 이벤트로 정의되지 않고 클래스에 대한 속성으로 정의됩니다. 따라서 `+=` 연산자를 사용하여 이러한 대리자를 구독하지 않고 대리자 개체를 속성에 할당합니다.

> [!TIP]
> C++ IntelliSense는 전체 대리자 시그니처를 보여 주지 않으므로 EventArgs 매개 변수의 특정 형식을 확인하는 데 도움이 되지 않습니다. 형식을 찾으려면 **개체 브라우저** 로 이동하고 대리자의 `Invoke` 메서드를 살펴보세요.

## <a name="creating-custom-delegates"></a>사용자 지정 대리자 만들기

사용자 고유의 대리자를 정의 하 여 이벤트 처리기를 정의 하거나 소비자가 사용자 지정 기능을 Windows 런타임 구성 요소에 전달할 수 있도록 할 수 있습니다. 다른 Windows 런타임 형식과 마찬가지로 public 대리자는 제네릭으로 선언 될 수 없습니다.

### <a name="declaration"></a>선언

대리자 선언은 대리자가 형식이라는 점을 제외하고 함수 선언과 유사합니다. 일반적으로 대리자는 네임스페이스 범위에서 선언하지만 클래스 선언에 대리자 선언을 중첩할 수도 있습니다. 다음 대리자는 `ContactInfo^` ^를 입력으로 사용하고 `Platform::String^`을 반환하는 모든 함수를 캡슐화합니다.

[!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]

대리자 형식을 선언한 후 해당 형식의 클래스 멤버 또는 해당 형식의 개체를 매개 변수로 사용하는 메서드를 선언할 수 있습니다. 메서드 또는 함수도 대리자 형식을 반환할 수 있습니다. 다음 예제에서는 `ToCustomString` 메서드가 대리자를 입력 매개 변수로 사용합니다. 이 메서드를 사용하면 클라이언트 코드가 `ContactInfo` 개체 공용 속성의 일부나 전부에서 문자열을 만드는 사용자 지정 함수를 제공할 수 있습니다.

[!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]

> [!NOTE]
> Windows 런타임 참조 형식과 마찬가지로 대리자 형식을 참조할 때 "^" 기호를 사용 합니다.

이벤트 선언에는 항상 대리자 형식이 있습니다. 이 예제에서는 Windows 런타임의 일반적인 대리자 형식 시그니처를 보여 줍니다.

[!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]

`Click` 클래스에서 `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` 이벤트는 `RoutedEventHandler`형식입니다. 자세한 내용은 [이벤트](../cppcx/events-c-cx.md)를 참조하세요.

클라이언트 코드는 먼저 `ref new` 를 사용하고 대리자 시그니처와 호환되는 람다를 제공하여 대리자 인스턴스를 만들고 사용자 지정 동작을 정의합니다.

[!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]

그런 다음 멤버 함수를 호출하고 대리자를 전달합니다. `ci` 는 `ContactInfo^` 인스턴스이고 `textBlock` 은 XAML `TextBlock^`이라고 가정합니다.

[!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]

다음 예제에서는 클라이언트 응용 프로그램이의 각 항목에 대해 대리자를 실행 하는 Windows 런타임 구성 요소의 공용 메서드에 사용자 지정 대리자를 전달 합니다 `Vector` .

[!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]

[!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]

### <a name="construction"></a>건설

이러한 개체에서 대리자를 생성할 수 있습니다.

- 람다

- 정적 함수

- 멤버 포인터

- std::function

다음 예제에서는 이러한 각각의 개체에서 대리자를 만드는 방법을 보여 줍니다. 대리자는 생성하는 데 사용된 개체 형식에 관계없이 똑같이 사용합니다.

[!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]

> [!WARNING]
> "this" 포인터를 캡처하는 람다를 사용할 경우 람다를 종료하기 전에 `-=` 연산자를 사용하여 이벤트에서 명시적으로 등록을 취소하세요. 자세한 내용은 [이벤트](../cppcx/events-c-cx.md)를 참조하세요.

### <a name="generic-delegates"></a>제네릭 대리자

C++/CX의 제네릭 대리자에는 제네릭 클래스의 선언과 유사한 제한이 있습니다. 이들은 public으로 선언할 수 없습니다. 전용 또는 내부 제네릭 대리자를 선언하고 이를 C++에서 사용할 수 있지만, .winmd 메타데이터로 내보내지 않으므로 .NET 또는 JavaScript 클라이언트에서는 사용할 수 없습니다. 다음 예제는 C++에서만 사용할 수 있는 제네릭 대리자를 선언합니다.

[!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]

다음 예제에서는 클래스 정의 내부에서 대리자의 특수화된 인스턴스를 선언합니다.

[!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]

## <a name="delegates-and-threads"></a>대리자 및 스레드

대리자는 함수 개체와 마찬가지로 나중에 실행하게 될 코드를 포함합니다. 대리자를 만들고 전달하는 코드와 대리자를 사용하고 실행하는 함수가 동일한 스레드에서 실행 중인 경우 작업이 비교적 단순합니다. 해당 스레드가 UI 스레드일 경우 대리자가 XAML 컨트롤과 같은 사용자 인터페이스 개체를 직접 조작할 수 있습니다.

클라이언트 앱이 스레드 아파트에서 실행 되는 Windows 런타임 구성 요소를 로드 하 고 해당 구성 요소에 대리자를 제공 하면 기본적으로 대리자가 STA 스레드에서 직접 호출 됩니다. 대부분의 Windows 런타임 구성 요소는 STA 또는 MTA에서 실행할 수 있습니다.

대리자를 실행하는 코드가 다른 스레드에서 실행 중인 경우(예: concurrency::task 개체의 컨텍스트 내) 공유 데이터에 대한 액세스 동기화 책임은 사용자에게 있습니다. 예를 들어 대리자에 Vector에 대한 참조가 포함되어 있고 XAML 컨트롤에 동일한 Vector에 대한 참조가 있는 경우 대리자와 XAML 컨트롤이 동시에 Vector에 액세스를 시도할 경우 발생할 수 있는 교착 상태나 경합 상태를 피하기 위해 조치를 취해야 합니다. 또한 대리자가 호출되기 전에 범위를 벗어날 수 있는 지역 변수 참조로 캡처를 시도하지 않도록 주의해야 합니다.

직접 만든 대리자가 생성된 스레드에서 다시 호출되고(예: MTA 아파트에서 실행되는 구성 요소로 전달하는 경우) 생성자와 동일한 스레드에서 호출되도록 하려면 두 번째 `CallbackContext` 매개 변수를 사용하는 대리자 생성자 오버로드를 사용하세요. 이 오버로드는 등록된 프록시/스텁이 있는 대리자에서만 사용하세요. Windows.winmd에 정의된 대리자가 모두 등록되는 것은 아닙니다.

.NET의 이벤트 처리기에 익숙하지 않다면 권장되는 방법은 실행하기 전에 이벤트의 로컬 복사본을 만드는 것입니다. 이렇게 함으로써 이벤트가 호출되기 전에 이벤트 처리기가 제거될 수 있는 경합 상태를 피할 수 있습니다. C++/CX에서는 이벤트 처리기가 추가 또는 제거될 때 새 처리기 목록이 생성되므로 이렇게 할 필요가 없습니다. 이벤트를 호출하기 전에 처리기 목록에서 C++ 개체가 참조 횟수를 증가시키므로 모든 처리기가 유효하도록 보장됩니다. 그러나 이는 한편으로 소비 스레드에서 이벤트 처리기를 제거했는데 게시 개체가 현재는 만료된 해당 목록 복사본에서 아직 작동 중인 경우 해당 처리기를 여전히 호출할 수 있음을 의미합니다. 이 게시 개체는 다음에 이벤트를 발생시킬 때까지 업데이트된 목록을 가져올 수 없습니다.

## <a name="see-also"></a>참고 항목

[유형 시스템](../cppcx/type-system-c-cx.md)<br/>
[C + +/CX 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[네임 스페이스 참조](../cppcx/namespaces-reference-c-cx.md)
