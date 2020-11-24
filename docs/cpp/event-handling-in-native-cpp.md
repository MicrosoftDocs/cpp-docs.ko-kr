---
title: 네이티브 C++에서 이벤트 처리
description: 네이티브 c + + 이벤트 처리에 Microsoft c + + 확장을 사용 하는 방법에 대해 알아봅니다.
ms.date: 11/20/2020
helpviewer_keywords:
- event handling [C++]
ms.openlocfilehash: 5ad9128b7ff596674c3b08687b722c81b7a10aa8
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483180"
---
# <a name="event-handling-in-native-c"></a>네이티브 C++에서 이벤트 처리

네이티브 c + + 이벤트 처리에서는를 지정 하 여 [event_source](../windows/attributes/event-source.md) 및 [event_receiver](../windows/attributes/event-receiver.md) 특성을 사용 하 여 이벤트 소스와 이벤트 수신기를 설정 `type` = `native` 합니다. 이러한 특성을 사용 하면 적용 되는 클래스가 이벤트를 발생 시키고 COM이 아닌 네이티브 컨텍스트에서 이벤트를 처리할 수 있습니다.

> [!NOTE]
> 네이티브 c + +의 이벤트 특성은 표준 c + +와 호환 되지 않습니다. 규칙 모드를 지정 하는 경우에는 컴파일되지 않습니다 [`/permissive-`](../build/reference/permissive-standards-conformance.md) .

## <a name="declaring-events"></a>이벤트 선언

이벤트 소스 클래스에서 메서드를 [`__event`](../cpp/event.md) 이벤트로 선언 하려면 메서드 선언에 키워드를 사용 합니다. 메서드를 선언 해야 하지만 정의 하지 않아야 합니다. 이 경우 컴파일러는 이벤트에 대해 메서드를 암시적으로 정의 하기 때문에 컴파일러 오류를 생성 합니다. 네이티브 이벤트는 매개 변수가 0개 이상인 메서드일 수 있습니다. 반환 형식은 **`void`** 또는 임의의 정수 계열 형식일 수 있습니다.

## <a name="defining-event-handlers"></a>이벤트 처리기 정의

이벤트 수신기 클래스에서 이벤트 처리기를 정의 합니다. 이벤트 처리기는 처리할 이벤트와 일치 하는 서명 (반환 형식, 호출 규칙 및 인수)이 포함 된 메서드입니다.

## <a name="hooking-event-handlers-to-events"></a>이벤트에 이벤트 처리기 후크

또한 이벤트 수신기 클래스에서 내장 함수를 사용 하 여 이벤트 처리기와 이벤트를 [`__hook`](../cpp/hook.md) 연결 하 고 [`__unhook`](../cpp/unhook.md) 이벤트 처리기에서 이벤트의 연결을 해제할 수 있습니다. 한 이벤트 처리기에 여러 이벤트를 후크하거나 한 이벤트에 여러 이벤트 처리기를 후크할 수 있습니다.

## <a name="firing-events"></a>이벤트 발생

이벤트를 발생 시키려면 이벤트 소스 클래스에서 이벤트로 선언 된 메서드를 호출 합니다. 처리기가 이벤트에 후크된 경우 처리기가 호출됩니다.

### <a name="native-c-event-code"></a>네이티브 c + + 이벤트 코드

다음 예제에서는 네이티브 C++에서 이벤트를 발생시키는 방법을 보여 줍니다. 예제를 컴파일 및 실행하려면 코드의 주석을 참조하십시오. Visual Studio IDE에서 코드를 빌드하려면 **`/permissive-`** 옵션이 꺼져 있는지 확인 합니다.

## <a name="example"></a>예제

### <a name="code"></a>코드

```cpp
// evh_native.cpp
// compile by using: cl /EHsc /W3 evh_native.cpp
#include <stdio.h>

[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};

[event_receiver(native)]
class CReceiver {
public:
   void MyHandler1(int nValue) {
      printf_s("MyHandler1 was called with value %d.\n", nValue);
   }

   void MyHandler2(int nValue) {
      printf_s("MyHandler2 was called with value %d.\n", nValue);
   }

   void hookEvent(CSource* pSource) {
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }

   void unhookEvent(CSource* pSource) {
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }
};

int main() {
   CSource source;
   CReceiver receiver;

   receiver.hookEvent(&source);
   __raise source.MyEvent(123);
   receiver.unhookEvent(&source);
}
```

### <a name="output"></a>출력

```Output
MyHandler2 was called with value 123.
MyHandler1 was called with value 123.
```

## <a name="see-also"></a>참조

[이벤트 처리](../cpp/event-handling.md)
