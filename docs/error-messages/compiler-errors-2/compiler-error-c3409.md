---
title: 컴파일러 오류 C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: d3800998ded1758ab1de92af689d9d4613c2c61e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502329"
---
# <a name="compiler-error-c3409"></a>컴파일러 오류 C3409

> 빈 특성 블록은 사용할 수 없습니다.

## <a name="remarks"></a>설명

대괄호가 컴파일러에서 [특성](../../windows/attributes/attributes-alphabetical-reference.md) 블록으로 해석 되었지만 특성이 없습니다.

람다 식 정의의 일부로 대괄호를 사용 하는 경우 컴파일러에서이 오류를 생성할 수 있습니다. 컴파일러가 대괄호가 람다 식 또는 특성 블록의 정의에 포함 되어 있는지 여부를 컴파일러에서 확인할 수 없는 경우이 오류가 발생 합니다. 람다 식에 대 한 자세한 내용은 [람다 식](../../cpp/lambda-expressions-in-cpp.md)을 참조 하세요.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 대괄호가 특성 블록의 일부인 경우:

   1. 특성 블록에 하나 이상의 특성을 제공 합니다.

   1. 특성 블록을 제거 합니다.

1. 대괄호가 람다 식의 일부인 경우 람다 식이 유효한 구문 규칙을 따르는지 확인 합니다.

   람다 식 구문에 대 한 자세한 내용은 [람다 식 구문](../../cpp/lambda-expression-syntax.md)을 참조 하세요.

## <a name="examples"></a>예

다음 예제에서는 C3409를 생성 합니다.

```cpp
// C3409.cpp
// compile with: /c
#include <windows.h>
[]   // C3409
class a {};

// OK
[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface x {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class b : public x {};
```

다음 예제에서는 람다 식에서 **`mutable`** 사양을 사용 하지만 매개 변수 목록을 제공 하지 않기 때문에 C3409를 생성 합니다. 컴파일러가 대괄호가 람다 식 또는 특성 블록의 정의에 포함 되는지 여부를 확인할 수 없습니다.

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>참고 항목

[특성도](../../windows/attributes/attributes-alphabetical-reference.md)<br/>
[람다 식](../../cpp/lambda-expressions-in-cpp.md)<br/>
[람다 식 구문](../../cpp/lambda-expression-syntax.md)
