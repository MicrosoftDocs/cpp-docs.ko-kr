---
title: __event
description: Microsoft c + + extension 키워드를 사용 하 여 네이티브 이벤트를 처리 하는 방법을 알아봅니다 `__event` .
ms.date: 11/20/2020
f1_keywords:
- __event_cpp
- __event
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.openlocfilehash: 1678699d9b66c1a49dd5ca2bb019a6229c37a031
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483145"
---
# <a name="__event-keyword"></a>`__event` 키워드로

이벤트를 선언합니다.

> [!NOTE]
> 네이티브 c + +의 이벤트 특성은 표준 c + +와 호환 되지 않습니다. 규칙 모드를 지정 하는 경우에는 컴파일되지 않습니다 [`/permissive-`](../build/reference/permissive-standards-conformance.md) .

## <a name="syntax"></a>구문

> **`__event`** *`member-function-declarator`* **`;`**\
> **`__event`** **`__interface`** *`interface-specifier`* **`;`**\
> **`__event`** *`data-member-declarator`* **`;`**

## <a name="remarks"></a>설명

Microsoft 전용 키워드는 **`__event`** 멤버 함수 선언, 인터페이스 선언 또는 데이터 멤버 선언에 적용할 수 있습니다. 그러나 키워드를 사용 하 여 **`__event`** 중첩 된 클래스의 멤버를 한정할 수는 없습니다.

이벤트 소스 및 수신기가 네이티브 C++ 또는 COM이거나 관리되는지(.NET Framework)에 따라 다음 구문을 이벤트로 사용할 수 있습니다.

| 네이티브 C++ | COM | 관리됨(.NET Framework) |
|--|--|--|
| 멤버 함수 | - | method |
| - | interface(인터페이스) | - |
| - | - | 데이터 멤버(data member) |

[`__hook`](../cpp/hook.md)이벤트 수신기에서를 사용 하 여 처리기 멤버 함수를 이벤트 멤버 함수와 연결 합니다. 키워드를 사용 하 여 이벤트를 만든 후에 **`__event`** 는 이벤트가 호출 될 때 이후에 해당 이벤트에 후크 된 모든 이벤트 처리기가 호출 됩니다.

**`__event`** 멤버 함수 선언에는 정의를 사용할 수 없습니다. 정의는 암시적으로 생성 되므로 이벤트 멤버 함수를 일반 멤버 함수인 것 처럼 호출할 수 있습니다.

> [!NOTE]
> 템플릿 기반 클래스 또는 구조체는 이벤트를 포함할 수 없습니다.

## <a name="native-events"></a>네이티브 이벤트

네이티브 이벤트는 멤버 함수입니다. 반환 형식은 일반적으로 `HRESULT` 또는 **`void`** 이지만을 비롯 한 모든 정수 계열 형식일 수 있습니다 **`enum`** . 이벤트가 정수 계열 반환 형식을 사용 하는 경우 이벤트 처리기가 0이 아닌 값을 반환 하면 오류 조건이 정의 됩니다. 이 경우 발생 하는 이벤트는 다른 대리자를 호출 합니다.

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

샘플 코드는 [네이티브 c + +에서 이벤트 처리](../cpp/event-handling-in-native-cpp.md) 를 참조 하세요.

## <a name="com-events"></a>COM 이벤트

COM 이벤트는 인터페이스입니다. 이벤트 소스 인터페이스에서 멤버 함수의 매개 변수는 매개 변수 여야 하지만 엄격 *하 게 적용* 되지 않습니다. 아웃 캐스트를 사용할 경우 *out* 매개 변수가 유용 하지 않기 때문입니다. *Out* 매개 변수를 사용 하는 경우 수준 1 경고가 발생 합니다.

반환 형식은 일반적으로 `HRESULT` 또는 **`void`** 이지만를 비롯 한 모든 정수 계열 형식일 수 있습니다 **`enum`** . 이벤트가 정수 계열 반환 형식을 사용 하 고 이벤트 처리기가 0이 아닌 값을 반환 하는 경우 오류 조건입니다. 발생 하는 이벤트는 다른 대리자에 대 한 호출을 중단 합니다. 컴파일러는 [`source`](../windows/attributes/source-cpp.md) 생성 된 IDL에서 이벤트 소스 인터페이스를로 자동으로 표시 합니다.

[`__interface`](../cpp/interface.md)COM 이벤트 원본의 경우 키워드는 항상 필수입니다 **`__event`** .

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

샘플 코드는 [COM에서 이벤트 처리](../cpp/event-handling-in-com.md) 를 참조 하세요.

## <a name="managed-events"></a>관리 되는 이벤트

새 구문의 이벤트 코딩에 대 한 자세한 내용은 [이벤트](../extensions/event-cpp-component-extensions.md)를 참조 하세요.

관리 되는 이벤트는 데이터 멤버 또는 멤버 함수입니다. 이벤트와 함께 사용 하는 경우 대리자의 반환 형식은 [공용 언어 사양과](/dotnet/standard/language-independence-and-language-independent-components)호환 되어야 합니다. 이벤트 처리기의 반환 형식은 대리자의 반환 형식과 일치해야 합니다. 대리자에 대 한 자세한 내용은 [대리자 및 이벤트](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)를 참조 하세요. 관리되는 이벤트가 데이터 멤버인 경우 그 형식은 대리자에 대한 포인터여야 합니다.

.NET Framework에서 데이터 멤버를 메서드(즉, 해당 대리자의 `Invoke` 메서드) 자체인 것처럼 취급할 수 있습니다. 이렇게 하기 위해 관리 되는 이벤트 데이터 멤버를 선언 하기 위해 대리자 형식을 미리 정의할 수 있습니다. 반면에 관리 되는 이벤트 메서드는 해당 하는 관리 되는 대리자 (이미 정의 되지 않은 경우)를 암시적으로 정의 합니다. 예를 들어 `OnClick`과 같은 이벤트 값을 다음과 같이 이벤트로 선언할 수 있습니다.

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

관리 되는 이벤트를 암시적으로 선언 하는 `add` 경우 `remove` 이벤트 처리기가 추가 되거나 제거 될 때 호출 되는 및 접근자를 지정할 수 있습니다. 클래스 외부에서 이벤트를 호출 (발생) 하는 멤버 함수를 정의할 수도 있습니다.

## <a name="example-native-events"></a>예: 네이티브 이벤트

```cpp
// EventHandling_Native_Event.cpp
// compile with: /c
[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};
```

## <a name="example-com-events"></a>예: COM 이벤트

```cpp
// EventHandling_COM_Event.cpp
// compile with: /c
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];

[ dual, uuid("00000000-0000-0000-0000-000000000002") ]
__interface IEventSource {
   [id(1)] HRESULT MyEvent();
};
[ coclass, uuid("00000000-0000-0000-0000-000000000003"),  event_source(com) ]
class CSource : public IEventSource {
public:
   __event __interface IEventSource;
   HRESULT FireEvent() {
      __raise MyEvent();
      return S_OK;
   }
};
```

## <a name="see-also"></a>참조

[어](../cpp/keywords-cpp.md)\
[이벤트 처리](../cpp/event-handling.md)\
[`event_source`](../windows/attributes/event-source.md)\
[`event_receiver`](../windows/attributes/event-receiver.md)\
[`__hook`](../cpp/hook.md)\
[`__unhook`](../cpp/unhook.md)\
[`__raise`](../cpp/raise.md)
