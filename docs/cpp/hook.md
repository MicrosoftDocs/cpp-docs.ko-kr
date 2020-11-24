---
title: __hook
description: Microsoft c + + extension 키워드를 사용 하 여 네이티브 이벤트를 처리 하는 방법을 알아봅니다 `__hook` .
ms.date: 11/20/2020
f1_keywords:
- __hook_cpp
- __hook
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.openlocfilehash: 2a2bde221c53f0e1d420e2ab3a88eb299f6c284c
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483258"
---
# <a name="__hook-keyword"></a>`__hook` 키워드로

처리기 메서드를 이벤트와 연결합니다.

> [!NOTE]
> 네이티브 c + +의 이벤트 특성은 표준 c + +와 호환 되지 않습니다. 규칙 모드를 지정 하는 경우에는 컴파일되지 않습니다 [`/permissive-`](../build/reference/permissive-standards-conformance.md) .

## <a name="syntax"></a>구문

```cpp
long __hook(
    &SourceClass::EventMethod,
    source,
    &ReceiverClass::HandlerMethod
    [, receiver = this]
);

long __hook(
    interface,
    source
);
```

### <a name="parameters"></a>매개 변수

*`&SourceClass::EventMethod`*\
이벤트 처리기 메서드를 후크할 이벤트 메서드에 대한 포인터입니다.

- 네이티브 c + + 이벤트: *`SourceClass`* 는 이벤트 소스 클래스 이며 *`EventMethod`* 이벤트입니다.

- COM 이벤트: *`SourceClass`* 는 이벤트 소스 인터페이스 이며 *`EventMethod`* 해당 메서드 중 하나입니다.

- 관리 되는 이벤트: 이벤트 *`SourceClass`* 소스 클래스 이며 *`EventMethod`* 이벤트입니다.

*`interface`*\
후크 되는 인터페이스 이름으로 *`receiver`* , *`layout_dependent`* 특성의 매개 변수가 인 COM 이벤트 수신기에만 해당 합니다 [`event_receiver`](../windows/attributes/event-receiver.md) **`true`** .

*`source`*\
이벤트 소스의 인스턴스에 대한 포인터입니다. `type`에 지정 된 코드에 따라 `event_receiver` 는 *`source`* 다음 형식 중 하나일 수 있습니다.

- 네이티브 이벤트 소스 개체 포인터입니다.

- `IUnknown`기반 포인터 (COM 원본)입니다.

- 관리되는 이벤트의 관리되는 개체 포인터입니다.

*`&ReceiverClass::HandlerMethod`*\
이벤트에 후크될 이벤트 처리기 메서드에 대한 포인터입니다. 처리기는 클래스의 메서드 또는 동일한에 대 한 참조로 지정 됩니다. 클래스 이름을 지정 하지 않으면에서 클래스가 호출 된 것으로 **`__hook`** 가정 합니다.

- 네이티브 c + + 이벤트: *`ReceiverClass`* 는 이벤트 수신기 클래스이 고는 `HandlerMethod` 처리기입니다.

- COM 이벤트: *`ReceiverClass`* 는 이벤트 수신기 인터페이스 이며 *`HandlerMethod`* 해당 처리기 중 하나입니다.

- 관리 되는 이벤트:는 *`ReceiverClass`* 이벤트 수신기 클래스이 고는 *`HandlerMethod`* 처리기입니다.

*`receiver`*\
필드 이벤트 수신기 클래스의 인스턴스에 대 한 포인터입니다. 수신기를 지정 하지 않는 경우 기본값은가 호출 되는 받는 사람 클래스 또는 구조체입니다 **`__hook`** .

## <a name="usage"></a>사용량

이벤트 수신기 클래스 외부의 main을 포함하여 모든 함수 범위에서 사용할 수 있습니다.

## <a name="remarks"></a>설명

이벤트 수신기에서 내장 함수를 사용 **`__hook`** 하 여 처리기 메서드를 이벤트 메서드와 연결 하거나 후크 합니다. 이렇게 하면 소스에서 지정된 이벤트를 발생시킬 때 지정된 처리기가 호출됩니다. 여러 처리기를 단일 이벤트에 후크하거나 여러 이벤트를 단일 처리기에 후크할 수 있습니다.

에는 두 가지 형태가 있습니다 **`__hook`** . 대부분의 경우, 특히 특성의 *layout_dependent* 매개 변수가 인 COM 이벤트 수신기에 대해 첫 번째 (4 개 인수) 형식을 사용할 수 있습니다 [`event_receiver`](../windows/attributes/event-receiver.md) **`false`** .

이러한 경우에는 메서드 중 하나에서 이벤트를 발생 시키기 전에 인터페이스의 모든 메서드를 후크 할 필요가 없습니다. 이벤트를 처리 하는 메서드만 후크 해야 합니다. 의 두 번째 (두 인수) 형식은 **`__hook`** COM 이벤트 수신기에만 사용할 수 있습니다 *`layout_dependent`* **`= true`** .

**`__hook`** long 값을 반환 합니다. 0이 아닌 반환 값은 오류가 발생했음을 나타냅니다(관리되는 이벤트가 예외를 throw함).

컴파일러는 이벤트가 있는지 확인하고 이벤트 시그니처가 대리자 시그니처와 일치하는지 확인합니다.

**`__hook`** **`__unhook`** COM 이벤트를 제외 하 고 이벤트 수신기 외부에서 및를 호출할 수 있습니다.

를 사용 하는 대신 **`__hook`** + = 연산자를 사용 합니다.

새 구문에서 관리 되는 이벤트를 코딩 하는 방법에 대 한 자세한 내용은을 참조 하십시오 [`event`](../extensions/event-cpp-component-extensions.md) .

> [!NOTE]
> 템플릿 기반 클래스 또는 구조체에 event를 포함시킬 수 없습니다.

## <a name="example"></a>예제

[네이티브 c + +에서 이벤트 처리](../cpp/event-handling-in-native-cpp.md) 및 샘플에 대 한 [COM에서 이벤트 처리](../cpp/event-handling-in-com.md) 를 참조 하세요.

## <a name="see-also"></a>참조

[어](../cpp/keywords-cpp.md)\
[이벤트 처리](../cpp/event-handling.md)\
[`event_source`](../windows/attributes/event-source.md)\
[`event_receiver`](../windows/attributes/event-receiver.md)\
[`__event`](../cpp/event.md)\
[`__unhook`](../cpp/unhook.md)\
[`__raise`](../cpp/raise.md)
