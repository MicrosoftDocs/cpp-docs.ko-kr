---
title: event_source (c + + COM 특성)
description: Microsoft c + + 확장 COM 특성을 사용 하는 방법을 알아봅니다 `event_source` .
ms.date: 11/20/2020
f1_keywords:
- vc-attr.event_source
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.openlocfilehash: 3cdfaaa86f8fc36bf0dc90d7961077546362a662
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483271"
---
# <a name="event_source-attribute"></a>`event_source` 특성

이벤트 소스를 만듭니다.

> [!NOTE]
> 네이티브 c + +의 이벤트 특성은 표준 c + +와 호환 되지 않습니다. 규칙 모드를 지정 하는 경우에는 컴파일되지 않습니다 [`/permissive-`](../../build/reference/permissive-standards-conformance.md) .

## <a name="syntax"></a>구문

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>매개 변수

*`type`*\
다음 값 중 하나의 열거형:

- `native` - 관리되지 않는 C/C++ 코드용(관리되지 않는 클래스에 대한 기본값).

- `com` - COM 코드용. `coclass`When *`type`* = `com` 를 사용 합니다. 이 값을 사용하려면 다음 헤더 파일을 포함해야 합니다.

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*`optimize`*\
*형식이* 인 경우 `native` `optimize=size` 클래스의 모든 이벤트에 대해 4 바이트의 저장소 (최소)가 있음을 나타내거나 `optimize=speed` (기본값), 4 * (이벤트 수) 바이트의 저장소가 있음을 나타내려면를 지정할 수 있습니다.

*`decorate`*\
*형식이* 인 경우 `native` `decorate=false` 병합 된 () 파일의 확장 된 이름에 *`.mrg`* 바깥쪽 클래스 이름이 포함 되지 않도록 지정할 수 있습니다. [`/Fx`](../../build/reference/fx-merge-injected-code.md) 에서 파일을 생성할 수 있습니다 *`.mrg`* . `decorate=false`기본값 인 경우 병합 된 파일에 정규화 된 형식 이름이 생성 됩니다.

## <a name="remarks"></a>설명

**`event_source`** C + + 특성은 해당 특성이 적용 되는 클래스 또는 구조가 이벤트 소스가 되도록 지정 합니다.

**`event_source`** 는 특성 및 키워드와 함께 사용 됩니다 [`event_receiver`](event-receiver.md) [`__event`](../../cpp/event.md) . `event_receiver`를 사용 하 여 이벤트 수신기를 만듭니다. **`__event`** 이벤트 원본 내에서 메서드를 사용 하 여 해당 메서드를 이벤트로 지정 합니다.

> [!NOTE]
> 템플릿 기반 클래스 또는 구조체에 event를 포함시킬 수 없습니다.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|--|--|
| **적용 대상** | **`class`**, **`struct`** |
| **불가능** | 아니요 |
| **필수 특성** | **`coclass`** 클릭할 `type`=`com` |
| **잘못된 특성** | 없음 |

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참조

[컴파일러 특성](compiler-attributes.md)\
[`event_receiver`](event-receiver.md)\
[`__event`](../../cpp/event.md)\
[`__hook`](../../cpp/hook.md)\
[`__unhook`](../../cpp/unhook.md)\
[클래스 특성](class-attributes.md)
