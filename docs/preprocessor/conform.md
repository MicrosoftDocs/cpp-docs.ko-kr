---
description: pragmaMicrosoft C/c + +의 준수 지시어에 대해 자세히 알아보세요.
title: 준수 pragma
ms.date: 01/22/2021
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragma, conform
no-loc:
- pragma
ms.openlocfilehash: baaeb41e2364daac8de91ca15251226bf3dd1e2a
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713703"
---
# <a name="conform-no-locpragma"></a>`conform` pragma

**C++ 전용**

컴파일러 옵션의 런타임 동작을 지정 합니다 [`/Zc:forScope`](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) .

## <a name="syntax"></a>구문

> **`#pragma conform(`***이름* [ **`, show`** ] [ **`,`** { **`on`**  |  **`off`** }] [[ **`,`** { **`push`**  |  **`pop`** }] [ **`,`** *식별자* [ **`,`** { **`on`**  |  **`off`** }]]]**`)`**

### <a name="parameters"></a>매개 변수

*이름의*\
수정할 컴파일러 옵션의 이름을 지정합니다. 유일 하 게  유효한 이름은 `forScope` 입니다.

**`show`**\
필드 컴파일 중에 경고 메시지를 통해 *이름* (true 또는 false)의 현재 설정을 표시 합니다. 예들 들어 `#pragma conform(forScope, show)`입니다.

**`on`**, **`off`**\
필드 *Name* 을로 설정 **`on`** 하면 [/zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 컴파일러 옵션을 사용할 수 있습니다. 기본값은 **`off`** 입니다.

**`push`**\
필드 *이름* 의 현재 값을 내부 컴파일러 스택에 푸시합니다. *식별자* 를 지정 하는 경우 **`on`** **`off`** 스택에 푸시할 *이름* 에 대해 또는 값을 지정할 수 있습니다. 예들 들어 `#pragma conform(forScope, push, myname, on)`입니다.

**`pop`**\
필드 *Name* 값을 내부 컴파일러 스택 맨 위의 값으로 설정 하 고 스택을 팝 합니다. 식별자가로 지정 된 경우에는 **`pop`** *식별자* 가 포함 된 레코드를 찾을 때까지 스택이 다시 팝 되며이는 팝 됩니다. 또한 스택의 다음 레코드에서 *이름* 에 대 한 현재 값이 *name* 의 새 값이 됩니다. 스택의 레코드에 없는 식별자를 지정 하 여를 지정 하는 경우 **`pop`**  **`pop`** 이 무시 됩니다.

*identifier*\
필드 또는 명령에 포함 될 수 있습니다 **`push`** **`pop`** . *식별자* 를 사용 하는 경우 **`on`** 또는 지정자를 **`off`** 사용할 수도 있습니다.

## <a name="example"></a>예제

```cpp
// pragma_directive_conform.cpp
// compile with: /W1
// C4811 expected
#pragma conform(forScope, show)
#pragma conform(forScope, push, x, on)
#pragma conform(forScope, push, x1, off)
#pragma conform(forScope, push, x2, off)
#pragma conform(forScope, push, x3, off)
#pragma conform(forScope, show)
#pragma conform(forScope, pop, x1)
#pragma conform(forScope, show)

int main() {}
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
