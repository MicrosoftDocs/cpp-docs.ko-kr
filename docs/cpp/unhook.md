---
title: __unhook
description: Microsoft c + + extension 키워드를 사용 하 여 네이티브 이벤트를 처리 하는 방법을 알아봅니다 `__unhook` .
ms.date: 11/04/2016
f1_keywords:
- __unhook
- __unhook_cpp
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.openlocfilehash: 74f8b814ea23c5513b7b73bf90ef59984742a266
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483323"
---
# <a name="__unhook-keyword"></a>`__unhook` 키워드로

이벤트에서 처리기 메서드를 분리 합니다.

> [!NOTE]
> 네이티브 c + +의 이벤트 특성은 표준 c + +와 호환 되지 않습니다. 규칙 모드를 지정 하는 경우에는 컴파일되지 않습니다 [`/permissive-`](../build/reference/permissive-standards-conformance.md) .

## <a name="syntax"></a>구문

```cpp
long  __unhook(
   &SourceClass::EventMethod,
   source,
   &ReceiverClass::HandlerMethod
   [, receiver = this]
);

long  __unhook(
   interface,
   source
);

long  __unhook(
   source
);
```

### <a name="parameters"></a>매개 변수

*`&SourceClass::EventMethod`*\
이벤트 처리기 메서드를 언후크할 이벤트 메서드의 포인터입니다.

- 네이티브 c + + 이벤트: *`SourceClass`* 는 이벤트 소스 클래스 이며 *`EventMethod`* 이벤트입니다.

- COM 이벤트: *`SourceClass`* 는 이벤트 소스 인터페이스 이며 *`EventMethod`* 해당 메서드 중 하나입니다.

- 관리 되는 이벤트: 이벤트 *`SourceClass`* 소스 클래스 이며 *`EventMethod`* 이벤트입니다.

*`interface`*\
특성의 *layout_dependent* 매개 변수가 인 COM 이벤트 수신기에 대해서만 *수신기* 에서 언 후크 되는 인터페이스 이름입니다 [`event_receiver`](../windows/attributes/event-receiver.md) **`true`** .

*`source`*\
이벤트 소스의 인스턴스에 대한 포인터입니다. `type`에 지정 된 코드에 따라 `event_receiver` *원본은* 다음 형식 중 하나일 수 있습니다.

- 네이티브 이벤트 소스 개체 포인터입니다.

- `IUnknown`기반 포인터 (COM 원본)입니다.

- 관리되는 이벤트의 관리되는 개체 포인터입니다.

*`&ReceiverClass::HandlerMethod`* 이벤트에서 언 후크 이벤트 처리기 메서드에 대 한 포인터입니다. 처리기는 클래스의 메서드 또는 동일한에 대 한 참조로 지정 됩니다. 클래스 이름을 지정 하지 않으면는 클래스를 **`__unhook`** 호출 하는 클래스를 가정 합니다.

- 네이티브 c + + 이벤트: *`ReceiverClass`* 는 이벤트 수신기 클래스이 고는 `HandlerMethod` 처리기입니다.

- COM 이벤트: *`ReceiverClass`* 는 이벤트 수신기 인터페이스 이며 *`HandlerMethod`* 해당 처리기 중 하나입니다.

- 관리 되는 이벤트:는 *`ReceiverClass`* 이벤트 수신기 클래스이 고는 *`HandlerMethod`* 처리기입니다.

*`receiver`* 필드 이벤트 수신기 클래스의 인스턴스에 대 한 포인터입니다. 수신기를 지정 하지 않는 경우 기본값은가 호출 되는 받는 사람 클래스 또는 구조체입니다 **`__unhook`** .

## <a name="usage"></a>사용량

는 `main` 이벤트 수신기 클래스 외부를 비롯 한 모든 함수 범위에서 사용할 수 있습니다.

## <a name="remarks"></a>설명

이벤트 수신기에서 내장 함수를 사용 **`__unhook`** 하 여 이벤트 메서드에서 처리기 메서드를 분리 하거나 "언 후크" 합니다.

에는 세 가지 형식이 있습니다 **`__unhook`** . 대부분 첫 번째(인수 4개) 형식을 사용할 수 있습니다. COM 이벤트 수신기에만 두 번째 (인수 2 개) 형식을 사용할 수 있으며 **`__unhook`** , 전체 이벤트 인터페이스를 언 후크합니다. 세 번째(인수 1개) 형식을 사용하여 지정된 소스에서 모든 대리자를 언후크할 수 있습니다.

0이 아닌 반환 값은 예외가 발생했음을 나타냅니다(관리되는 이벤트가 예외를 throw함).

**`__unhook`** 아직 후크 되지 않은 이벤트 및 이벤트 처리기에서를 호출 하는 경우에는 아무런 영향을 주지 않습니다.

컴파일할 때 컴파일러는 이벤트가 있는지 확인하고 지정된 처리기를 사용하여 매개 변수 형식을 검사합니다.

**`__hook`** **`__unhook`** COM 이벤트를 제외 하 고 이벤트 수신기 외부에서 및를 호출할 수 있습니다.

를 사용 하는 대신 **`__unhook`** -= 연산자를 사용 합니다.

새 구문에서 관리 되는 이벤트를 코딩 하는 방법에 대 한 자세한 내용은 [이벤트](../extensions/event-cpp-component-extensions.md)를 참조 하세요.

> [!NOTE]
> 템플릿 기반 클래스 또는 구조체에 event를 포함시킬 수 없습니다.

## <a name="example"></a>예제

[네이티브 c + +에서 이벤트 처리](../cpp/event-handling-in-native-cpp.md) 및 샘플에 대 한 [COM에서 이벤트 처리](../cpp/event-handling-in-com.md) 를 참조 하세요.

## <a name="see-also"></a>참조

[어](../cpp/keywords-cpp.md)\
[`event_source`](../windows/attributes/event-source.md)\
[`event_receiver`](../windows/attributes/event-receiver.md)\
[`__event`](../cpp/event.md)\
[`__hook`](../cpp/hook.md)\
[`__raise`](../cpp/raise.md)
