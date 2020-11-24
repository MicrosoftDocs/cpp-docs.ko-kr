---
title: COM에서 이벤트 처리
description: COM 용 Microsoft c + + 확장 이벤트 처리를 사용 하는 방법을 알아봅니다.
ms.date: 11/20/2020
helpviewer_keywords:
- event handling [C++], COM
- event handling [C++], about event handling
- declaring events
- event handlers [C++], COM
- event handlers
- COM, events
- event receivers, in event handling
- event handling [C++]
- hooking events
- event receivers, name and signature matching
- event sources, in event handling
- declaring events, in COM
- declaring events, event handling in COM
ms.openlocfilehash: 0c664f052fe211c88ad097c9d2617ec47f180eff
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483115"
---
# <a name="event-handling-in-com"></a>COM에서 이벤트 처리

COM 이벤트 처리에서는 및 특성을 사용 하 여 각각을 지정 하 여 이벤트 소스와 이벤트 수신기를 설정 [`event_source`](../windows/attributes/event-source.md) [`event_receiver`](../windows/attributes/event-receiver.md) `type` = `com` 합니다. 이러한 특성은 사용자 지정, 디스패치 및 이중 인터페이스에 대 한 적절 한 코드를 삽입 합니다. 삽입 된 코드를 사용 하 여 특성을 사용 하는 클래스는 이벤트를 발생 시키고 COM 연결 지점은 이벤트를 처리할 수 있습니다.

> [!NOTE]
> 네이티브 c + +의 이벤트 특성은 표준 c + +와 호환 되지 않습니다. 규칙 모드를 지정 하는 경우에는 컴파일되지 않습니다 [`/permissive-`](../build/reference/permissive-standards-conformance.md) .

## <a name="declaring-events"></a>이벤트 선언

이벤트 소스 클래스에서 [`__event`](../cpp/event.md) 인터페이스 선언에 키워드를 사용 하 여 해당 인터페이스의 메서드를 이벤트로 선언 합니다. 해당 인터페이스의 이벤트는 이를 인터페이스 메서드로 호출할 때 발생합니다. 이벤트 인터페이스의 메서드는 0 개 이상의 매개 변수를 가질 수 있습니다 .이 *매개 변수는 모두 매개 변수* 여야 합니다. 반환 형식은 void 또는 모든 정수 계열 형식이 될 수 있습니다.

## <a name="defining-event-handlers"></a>이벤트 처리기 정의

이벤트 수신기 클래스에서 이벤트 처리기를 정의 합니다. 이벤트 처리기는 처리할 이벤트와 일치 하는 서명 (반환 형식, 호출 규칙 및 인수)이 포함 된 메서드입니다. COM 이벤트의 경우 호출 규칙은와 일치 하지 않아도 됩니다. 자세한 내용은 아래의 [레이아웃 종속 COM 이벤트](#vcconeventhandlingincomanchorlayoutdependentcomevents) 를 참조 하세요.

## <a name="hooking-event-handlers-to-events"></a>이벤트에 이벤트 처리기 후크

또한 이벤트 수신기 클래스에서 내장 함수를 사용 하 여 이벤트 처리기와 이벤트를 [`__hook`](../cpp/hook.md) 연결 하 고 [`__unhook`](../cpp/unhook.md) 이벤트 처리기에서 이벤트의 연결을 해제할 수 있습니다. 한 이벤트 처리기에 여러 이벤트를 후크하거나 한 이벤트에 여러 이벤트 처리기를 후크할 수 있습니다.

> [!NOTE]
> 일반적으로 COM 이벤트 수신기가 이벤트 소스 인터페이스 정의에 액세스할 수 있게 만드는 두 가지 방법이 있습니다. 첫 번째 방법은 아래와 같이 공용 헤더 파일을 공유하는 것입니다. 두 번째는 [#import](../preprocessor/hash-import-directive-cpp.md) 를 가져오기 한정자와 함께 사용 하는 것입니다. `embedded_idl` 따라서 특성 생성 코드를 유지 하 여 이벤트 원본 형식 라이브러리가 .tlh 파일에 기록 됩니다.

## <a name="firing-events"></a>이벤트 발생

이벤트를 발생 시키려면 **`__event`** 이벤트 소스 클래스의 키워드를 사용 하 여 선언 된 인터페이스에서 메서드를 호출 합니다. 처리기가 이벤트에 후크된 경우 처리기가 호출됩니다.

### <a name="com-event-code"></a>COM 이벤트 코드

다음 예제에서는 COM 클래스에서 이벤트를 발생시키는 방법을 보여 줍니다. 예제를 컴파일 및 실행하려면 코드의 주석을 참조하십시오.

```cpp
// evh_server.h
#pragma once

[ dual, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IEvents {
   [id(1)] HRESULT MyEvent([in] int value);
};

[ dual, uuid("00000000-0000-0000-0000-000000000002") ]
__interface IEventSource {
   [id(1)] HRESULT FireEvent();
};

class DECLSPEC_UUID("530DF3AD-6936-3214-A83B-27B63C7997C4") CSource;
```

서버는 다음과 같습니다.

```cpp
// evh_server.cpp
// compile with: /LD
// post-build command: Regsvr32.exe /s evh_server.dll
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include "evh_server.h"

[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];

[coclass, event_source(com), uuid("530DF3AD-6936-3214-A83B-27B63C7997C4")]
class CSource : public IEventSource {
public:
   __event __interface IEvents;

   HRESULT FireEvent() {
      __raise MyEvent(123);
      return S_OK;
   }
};
```

클라이언트는 다음과 같습니다.

```cpp
// evh_client.cpp
// compile with: /link /OPT:NOREF
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <stdio.h>
#include "evh_server.h"

[ module(name="EventReceiver") ];

[ event_receiver(com) ]
class CReceiver {
public:
   HRESULT MyHandler1(int nValue) {
      printf_s("MyHandler1 was called with value %d.\n", nValue);
      return S_OK;
   }

   HRESULT MyHandler2(int nValue) {
      printf_s("MyHandler2 was called with value %d.\n", nValue);
      return S_OK;
   }

   void HookEvent(IEventSource* pSource) {
      __hook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler1);
      __hook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler2);
   }

   void UnhookEvent(IEventSource* pSource) {
      __unhook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler1);
      __unhook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler2);
   }
};

int main() {
   // Create COM object
   CoInitialize(NULL);
   {
      IEventSource* pSource = 0;
      HRESULT hr = CoCreateInstance(__uuidof(CSource), NULL,         CLSCTX_ALL, __uuidof(IEventSource), (void **) &pSource);
      if (FAILED(hr)) {
         return -1;
      }

      // Create receiver and fire event
      CReceiver receiver;
      receiver.HookEvent(pSource);
      pSource->FireEvent();
      receiver.UnhookEvent(pSource);
   }
   CoUninitialize();
   return 0;
}
```

### <a name="output"></a>출력

```Output
MyHandler1 was called with value 123.
MyHandler2 was called with value 123.
```

## <a name="layout-dependent-com-events"></a><a name="vcconeventhandlingincomanchorlayoutdependentcomevents"></a> 레이아웃 종속 COM 이벤트

레이아웃 종속성은 COM 프로그래밍에만 문제가 됩니다. 네이티브 및 관리 되는 이벤트 처리에서 처리기의 서명 (반환 형식, 호출 규칙 및 인수)은 해당 이벤트와 일치 해야 하지만 처리기 이름이 해당 이벤트와 일치 하지 않아도 됩니다.

그러나 COM 이벤트 처리에서 *`layout_dependent`* 의 매개 변수를로 설정 하면 `event_receiver` **`true`** 이름 및 서명 일치가 적용 됩니다. 이벤트 수신기 및 후크된 이벤트에서 처리기의 이름과 서명은 정확히 일치 해야 합니다.

*`layout_dependent`* 가로 설정 되 면 호출 하는 **`false`** 규칙 및 저장소 클래스 (가상, 정적 등)를 혼합 하 여 발생 시킬 수 있습니다. 이를 위해서는 약간 더 효율적 *`layout_dependent`* = **`true`** 입니다.

예를 들어, `IEventSource`가 다음 메서드를 사용하도록 정의되어 있다고 가정합니다.

```cpp
[id(1)] HRESULT MyEvent1([in] int value);
[id(2)] HRESULT MyEvent2([in] int value);
```

이벤트 소스의 형태가 다음과 같다고 가정합니다.

```cpp
[coclass, event_source(com)]
class CSource : public IEventSource {
public:
   __event __interface IEvents;

   HRESULT FireEvent() {
      MyEvent1(123);
      MyEvent2(123);
      return S_OK;
   }
};
```

그런 다음 이벤트 수신기에서 `IEventSource`의 메서드에 후크된 처리기가 다음과 같이 해당 이름과 시그니처를 일치시켜야 합니다.

```cpp
[coclass, event_receiver(com, true)]
class CReceiver {
public:
   HRESULT MyEvent1(int nValue) {  // name and signature matches MyEvent1
      ...
   }
   HRESULT MyEvent2(E c, char* pc) {  // signature doesn't match MyEvent2
      ...
   }
   HRESULT MyHandler1(int nValue) {  // name doesn't match MyEvent1 (or 2)
      ...
   }
   void HookEvent(IEventSource* pSource) {
      __hook(IFace, pSource);  // Hooks up all name-matched events
                               // under layout_dependent = true
      __hook(&IFace::MyEvent1, pSource, &CReceive::MyEvent1);   // valid
      __hook(&IFace::MyEvent2, pSource, &CSink::MyEvent2);   // not valid
      __hook(&IFace::MyEvent1, pSource, &CSink:: MyHandler1); // not valid
   }
};
```

## <a name="see-also"></a>참조

[이벤트 처리](../cpp/event-handling.md)
