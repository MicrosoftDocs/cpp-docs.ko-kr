---
title: event 키워드 (c + +/CLI 및 c + +/CX)
description: Microsoft c + + 구성 요소 확장 키워드를 사용 하는 방법을 알아봅니다 `event` .
ms.date: 11/20/2020
ms.topic: reference
f1_keywords:
- event
- event_cpp
helpviewer_keywords:
- event keyword [C++]
ms.openlocfilehash: 6a2fa97140f747b4afc380b57f8f7c71f08875db
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483245"
---
# <a name="event-keyword-ccli-and-ccx"></a>`event` 키워드 (c + +/CLI 및 c + +/CX)

**`event`** 키워드는 이벤트를 선언 합니다 .이 *이벤트* 는 관심 항목이 발생 한 등록 된 구독자 (*이벤트 처리기*)에 대 한 알림입니다.

## <a name="all-runtimes"></a>모든 런타임

C++/CX에서는 ‘이벤트 멤버’ 또는 ‘이벤트 블록’ 선언을 지원합니다. 이벤트 멤버는 이벤트 블록을 선언하기 위한 약칭입니다. 기본적으로는 이벤트 멤버는 이벤트 블록에서 명시적으로 선언된 `add`, `remove` 및 `raise` 함수를 선언합니다. 이벤트 멤버의 함수를 사용자 지정하려면 대신에 이벤트 블록을 선언하고 필요한 함수를 재정의합니다.

### <a name="syntax"></a>구문

```cpp
// event data member
modifier event delegate^ event_name;

// event block
modifier event delegate^ event_name
{
   modifier return_value add(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>매개 변수

*modifier*\
이벤트 선언 또는 이벤트 접근자 메서드에 사용할 수 있는 한정자입니다.  가능한 값은 **`static`** 및 **`virtual`** 입니다.

*대리자나*\
이벤트 처리기가 시그니처와 일치해야 하는 [대리자](delegate-cpp-component-extensions.md)입니다.

*event_name*\
이벤트의 이름입니다.

*return_value*\
이벤트 접근자 메서드의 반환 값입니다.  확인할 수 있도록 반환 형식은 여야 합니다 **`void`** .

*변수의*\
(선택 사항) *delegate* 매개 변수의 시그니처와 일치하는 `raise` 메서드의 매개 변수입니다.

### <a name="remarks"></a>설명

이벤트는 대리자와 *이벤트 처리기* 를 연결 하는 것입니다. 이벤트 처리기는 이벤트가 트리거될 때 응답 하는 멤버 함수입니다. 이를 통해 모든 클래스의 클라이언트는 대리자의 시그니처와 반환 형식과 일치 하는 메서드를 등록할 수 있습니다.

이벤트 선언에는 다음 두 가지 종류가 있습니다.

*이벤트 데이터 멤버*\
컴파일러에서는 대리자 형식의 멤버 형식으로 이벤트에 대한 스토리지를 자동으로 만들고 내부 `add`, `remove` 및 `raise` 멤버 함수를 만듭니다. 이벤트 데이터 멤버는 클래스 내에 선언되어야 합니다. 대리자의 반환 형식은 이벤트 처리기의 반환 형식과 일치해야 합니다.

*이벤트 블록*\
이벤트 블록을 사용하여 `add`, `remove` 및 `raise` 메서드의 동작을 명시적으로 선언 및 사용자 지정할 수 있습니다.

`operator +=`및 `operator -=` 를 사용 하 여 이벤트 처리기를 추가 및 제거 하거나, `add` 및 메서드를 `remove` 명시적으로 호출할 수 있습니다.

**`event`** 는 상황에 맞는 키워드입니다. 자세한 내용은 상황에 맞는 [키워드](context-sensitive-keywords-cpp-component-extensions.md)를 참조 하세요.

## <a name="windows-runtime"></a>Windows 런타임

### <a name="remarks"></a>설명

자세한 내용은 [이벤트(C++/CX)](../cppcx/events-c-cx.md)를 참조하세요.

이벤트 처리기를 추가 하 고 나중에 제거 하려면 `EventRegistrationToken` 작업에서 반환 되는 구조를 저장 합니다 `add` . 그런 다음 작업에서 저장 된 구조체를 사용 하 여 `remove` `EventRegistrationToken` 제거할 이벤트 처리기를 식별 합니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

**event** 키워드를 사용하여 이벤트를 선언할 수 있습니다. 이벤트는 특정 상황이 발생할 때 클래스가 알림을 제공하는 한 가지 방법입니다.

### <a name="syntax"></a>구문

```cpp
// event data member
modifier event delegate^ event_name;

// event block
modifier event delegate^ event_name
{
   modifier return_value add(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>매개 변수

*modifier*\
이벤트 선언 또는 이벤트 접근자 메서드에 사용할 수 있는 한정자입니다.  가능한 값은 **`static`** 및 **`virtual`** 입니다.

*대리자나*\
이벤트 처리기가 시그니처와 일치해야 하는 [대리자](delegate-cpp-component-extensions.md)입니다.

*event_name*\
이벤트의 이름입니다.

*return_value*\
이벤트 접근자 메서드의 반환 값입니다.  확인할 수 있도록 반환 형식은 여야 합니다 **`void`** .

*변수의*\
(선택 사항) *delegate* 매개 변수의 시그니처와 일치하는 `raise` 메서드의 매개 변수입니다.

### <a name="remarks"></a>설명

이벤트는 대리자와 *이벤트 처리기* 를 연결 하는 것입니다. 이벤트 처리기는 이벤트가 트리거될 때 응답 하는 멤버 함수입니다. 이를 통해 모든 클래스의 클라이언트는 기본 대리자의 시그니처와 반환 형식에 일치 하는 메서드를 등록할 수 있습니다.

대리자에는 하나 이상의 연결 된 메서드가 있을 수 있습니다. 이러한 메서드는 코드에서 이벤트가 발생 했음을 나타내는 경우 호출 됩니다. 한 프로그램의 이벤트를 .NET Framework 공용 언어 런타임을 대상으로 하는 다른 프로그램에서 사용 가능하게 설정할 수 있습니다.

이벤트 선언에는 다음 두 가지 종류가 있습니다.

*이벤트 데이터 멤버*\
컴파일러는 데이터 멤버 이벤트의 저장소를 대리자 형식의 멤버로 만듭니다. 이벤트 데이터 멤버는 클래스 내에 선언되어야 합니다. *간단한 이벤트* 라고도 합니다. 예제는 코드 샘플을 참조 하세요.

*이벤트 블록*\
이벤트 블록을 사용 하면, `add` `remove` `raise` 및 메서드를 구현 하 여, 및 메서드의 동작 `add` 을 `remove` 사용자 지정할 수 있습니다 `raise` . `add`, 및 메서드의 시그니처는 `remove` `raise` 대리자의 시그니처와 일치 해야 합니다. 이벤트 차단 이벤트는 데이터 멤버가 아닙니다. 데이터 멤버로 사용 하면 컴파일러 오류가 생성 됩니다.

이벤트 처리기의 반환 형식은 대리자의 반환 형식과 일치해야 합니다.

.NET Framework에서 데이터 멤버를 메서드(즉, 해당 대리자의 `Invoke` 메서드) 자체인 것처럼 취급할 수 있습니다. 이렇게 하기 위해 관리 되는 이벤트 데이터 멤버를 선언 하기 위해 대리자 형식을 미리 정의할 수 있습니다. 반면에 관리 되는 이벤트 메서드는 해당 하는 관리 되는 대리자 (이미 정의 되지 않은 경우)를 암시적으로 정의 합니다. 예제는이 문서의 끝에 있는 코드 샘플을 참조 하세요.

관리 되는 이벤트를 선언할 때 및 `add` 연산자를 `remove` 사용 하 여 이벤트 처리기를 추가 하거나 제거할 때 호출 되는 및 접근자를 지정할 수 있습니다 **`+=`** **`-=`** . `add`, `remove` 및 메서드를 `raise` 명시적으로 호출할 수 있습니다.

Microsoft c + +에서 이벤트를 만들고 사용 하려면 다음 단계를 수행 해야 합니다.

1. 대리자를 만들거나 식별합니다. 사용자 고유의 이벤트를 정의 하는 경우 키워드와 함께 사용할 대리자도 있는지도 확인 해야 합니다 **`event`** . 예를 들어 이벤트가 미리 정의되어 있으면 .NET Framework에서 이벤트 소비자는 대리자의 이름만 알면 됩니다.

2. 다음을 포함하는 클래스를 만듭니다.

   - 대리자에서 생성된 이벤트.

   - 필드 키워드로 선언 된 대리자의 인스턴스가 있는지 확인 하는 메서드입니다 **`event`** . 이외에는 이 논리가 이벤트를 실행하는 코드에 배치되어야 합니다.

   - 이벤트를 호출하는 메서드. 이들 메서드는 일부 기본 클래스 기능의 재정의일 수 있습니다.

   이 클래스는 이벤트를 정의합니다.

3. 메서드를 이벤트에 연결하는 하나 이상의 클래스를 정의합니다. 이러한 각 클래스는 하나 이상의 메서드를 기본 클래스의 이벤트와 연결합니다.

4. 이벤트를 사용합니다.

   - 이벤트 선언을 포함하는 클래스의 개체를 만듭니다.

   - 이벤트 정의를 포함하는 클래스의 개체를 만듭니다.

C + +/CLI 이벤트에 대 한 자세한 내용은 [인터페이스의 이벤트](../dotnet/how-to-use-events-in-cpp-cli.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예

다음 코드 예제에서는 대리자, 이벤트 및 이벤트 처리기의 쌍을 선언 하는 방법을 보여 줍니다. 이 예제에서는 이벤트 처리기를 구독 (추가) 하 고 호출한 다음 구독 취소 (제거) 하는 방법을 보여 줍니다.

```cpp
// mcppv2_events.cpp
// compile with: /clr
using namespace System;

// declare delegates
delegate void ClickEventHandler(int, double);
delegate void DblClickEventHandler(String^);

// class that defines events
ref class EventSource {
public:
   event ClickEventHandler^ OnClick;   // declare the event OnClick
   event DblClickEventHandler^ OnDblClick;   // declare OnDblClick

   void FireEvents() {
      // raises events
      OnClick(7, 3.14159);
      OnDblClick("Hello");
   }
};

// class that defines methods that will called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }

   void OnMyDblClick(String^ str) {
      Console::WriteLine("OnDblClick: {0}", str);
   }
};

int main() {
   EventSource ^ MyEventSource = gcnew EventSource();
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   MyEventSource->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick += gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);

   // invoke events
   MyEventSource->FireEvents();

   // unhook handler to event
   MyEventSource->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick -= gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);
}
```

```Output
OnClick: 7, 3.14159

OnDblClick: Hello
```

다음 코드 예제에서는 `raise` trivial 이벤트의 메서드를 생성 하는 데 사용 되는 논리를 보여 줍니다. 이벤트에 하나 이상의 구독자가 있는 경우 `raise` 메서드를 명시적 또는 암시적으로 호출하면 대리자가 호출됩니다. 대리자의 반환 형식이 **`void`** 이 아니며 이벤트 구독자가 없는 경우이 `raise` 메서드는 대리자 형식에 대 한 기본값을 반환 합니다. 이벤트 구독자가 없는 경우 `raise` 메서드를 즉시 반환 하 고 예외가 발생 하지 않습니다. 대리자 반환 형식이가 아니면 **`void`** 대리자 형식이 반환 됩니다.

```cpp
// trivial_events.cpp
// compile with: /clr /c
using namespace System;
public delegate int Del();
public ref struct C {
   int i;
   event Del^ MyEvent;

   void FireEvent() {
      i = MyEvent();
   }
};

ref struct EventReceiver {
   int OnMyClick() { return 0; }
};

int main() {
   C c;
   c.i = 687;

   c.FireEvent();
   Console::WriteLine(c.i);
   c.i = 688;

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();
   c.MyEvent += gcnew Del(MyEventReceiver, &EventReceiver::OnMyClick);
   Console::WriteLine(c.i);
}
```

```Output
0

688
```

## <a name="see-also"></a>참조

[.NET 및 UWP용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
