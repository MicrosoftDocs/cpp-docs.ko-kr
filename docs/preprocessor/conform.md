---
title: 준수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- conform_CPP
- vc-pragma.conform
dev_langs:
- C++
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05b1f9fef458b8c21de9eb3942730ff901d3922e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071234"
---
# <a name="conform"></a>준수
**C + + 전용**

런타임 동작을 지정 합니다 [/zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 컴파일러 옵션입니다.

## <a name="syntax"></a>구문

> **#pragma 준수 (** *이름* [**, 표시** ] [**를** { **온** | **해제** }] [[**,** { **푸시** | **pop** }] [**하십시오** *식별자* ]] **)**

### <a name="parameters"></a>매개 변수

*name*<br/>
수정할 컴파일러 옵션의 이름을 지정합니다. 유일한 유효 *이름을* 는 `forScope`합니다.

**Show**<br/>
(선택 사항) 현재 설정을 사용 하면 *이름을* (true 또는 false)를 컴파일하는 동안 경고 메시지를 통해 표시 됩니다. 예를 들어, `#pragma conform(forScope, show)`을 입력합니다.

**온**, **해제**<br/>
(선택 사항) 설정 *이름을* 에 **에** 사용 하도록 설정 합니다 [/zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 컴파일러 옵션입니다. 기본값은 **해제**합니다.

**push**<br/>
(선택 사항) 현재 값을 푸시합니다 *이름을* 내부 컴파일러 스택으로 합니다. 지정 하는 경우 *식별자*를 지정할 수 있습니다는 **에** 또는 **해제** 값 *이름* 스택으로 푸시 하도록 합니다. 예를 들어, `#pragma conform(forScope, push, myname, on)`을 입력합니다.

**pop**<br/>
(선택 사항) 값을 설정 *이름을* 내부 컴파일러 스택 및 다음 스택 팝의 맨 위에 있는 값입니다. 식별자가 지정 된 경우 **pop**, 스택을 사용 하 여 레코드를 찾을 때까지 다시 팝 됩니다 *식별자*에 있는 팝 됩니다;에 대 한 현재 값을 *이름* 에서 스택의 다음 레코드에 대 한 새 값이 됩니다 *이름을*입니다. 지정 하는 경우 **pop** 사용 하 여는 *식별자* 스택의 레코드에 없는 합니다 **pop** 무시 됩니다.

*identifier*<br/>
(선택 사항) 포함할 수는 **푸시** 또는 **pop** 명령입니다. 하는 경우 *식별자* 를 사용 하면 **에** 또는 **해제** 지정자를 사용할 수도 있습니다.

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

[Pragma 지시문 및 __Pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)