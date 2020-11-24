---
title: event_receiver (c + + COM 특성)
description: Microsoft c + + 확장 COM 특성을 사용 하는 방법을 알아봅니다 `event_receiver` .
ms.date: 11/20/2020
f1_keywords:
- vc-attr.event_receiver
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.openlocfilehash: 8ed6ef6113d72a9565b275dff4e035dc56f11e82
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483284"
---
# <a name="event_receiver-attribute"></a>`event_receiver` 특성

이벤트 수신기(싱크)를 만듭니다.

> [!NOTE]
> 네이티브 c + +의 이벤트 특성은 표준 c + +와 호환 되지 않습니다. 규칙 모드를 지정 하는 경우에는 컴파일되지 않습니다 [`/permissive-`](../../build/reference/permissive-standards-conformance.md) .

## <a name="syntax"></a>구문

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>매개 변수

*`type`*\
다음 값 중 하나의 열거형:

- `native` 관리 되지 않는 C/c + + 코드의 경우 (네이티브 클래스의 경우 기본값)

- `com` - COM 코드용. 이 값을 사용 하려면 다음 헤더 파일을 포함 해야 합니다.

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*`layout_dependent`*\
*`layout_dependent`* Com 인 경우에만 지정 `type` = **com** 합니다. *`layout_dependent`* 는 부울입니다.

- **`true`** 는 이벤트 수신기의 대리자 시그니처가 이벤트 원본에서 후크 된 대리자와 정확히 일치 해야 함을 의미 합니다. 이벤트 수신기 처리기 이름은 관련 이벤트 원본 인터페이스에 지정 된 이름과 일치 해야 합니다. `coclass` *`layout_dependent`* 가 인 경우를 사용 **`true`** 합니다. 을 지정 하는 것이 약간 더 효율적 **`true`** 입니다.

- **`false`** (기본값)은 호출 규칙 및 저장소 클래스 ( `virtual` , `static` 및 기타)가 이벤트 메서드와 처리기를 일치 시킬 필요가 없음을 의미 합니다. 처리기 이름도 이벤트 원본 인터페이스 메서드 이름과 일치 하지 않아도 됩니다.

## <a name="remarks"></a>설명

**`event_receiver`** C + + 특성은 Microsoft c + + 통합 이벤트 모델을 사용 하 여이 특성이 적용 되는 클래스 또는 구조가 이벤트 수신기가 되도록 지정 합니다.

**`event_receiver`** 는 [`event_source`](event-source.md) 특성 및 및 키워드와 함께 사용 됩니다 [`__hook`](../../cpp/hook.md) [`__unhook`](../../cpp/unhook.md) . `event_source`를 사용 하 여 이벤트 원본을 만듭니다. 이벤트 **`__hook`** 수신기의 메서드 내에서를 사용 하 여 이벤트 수신기 메서드를 이벤트 소스의 이벤트에 연결 합니다 ("후크"). **`__unhook`** 를 사용 하 여 연관을 해제 합니다.

*`layout_dependent`* 는 COM 이벤트 수신기 ()에 대해서만 지정 됩니다 `type` = **`com`** . 의 기본값은 *`layout_dependent`* **`false`** 입니다.

> [!NOTE]
> 템플릿 기반 클래스 또는 구조체에 event를 포함시킬 수 없습니다.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|--|--|
| **적용 대상** | **`class`**, **`struct`** |
| **불가능** | 아니요 |
| **필수 특성** | `coclass` 클릭할 *`layout_dependent`*=**`true`** |
| **잘못된 특성** | 없음 |

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조 하세요.

## <a name="see-also"></a>참조

[컴파일러 특성](compiler-attributes.md)\
[`event_source`](event-source.md)\
[`__event`](../../cpp/event.md)\
[`__hook`](../../cpp/hook.md)\
[`__unhook`](../../cpp/unhook.md)\
[클래스 특성](class-attributes.md)
