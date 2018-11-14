---
title: 컴파일러 오류 C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: b6ceb6f2e8700a5459dbd01db443ef90de314b5e
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330088"
---
# <a name="compiler-error-c3409"></a>컴파일러 오류 C3409

> 빈 특성 블록 허용 되지 않습니다.

## <a name="remarks"></a>설명

대괄호는 컴파일러에 의해 해석 된를 [특성](../../windows/cpp-attributes-reference.md) 블록 하지만 특성이 없는 찾을 수 없습니다.

컴파일러는 람다 식 정의의 일부로 대괄호를 사용 하는 경우이 오류를 생성할 수 있습니다. 이 오류는 컴파일러가 요소를 대괄호로 묶은 특성 블록 또는 람다 식의 정의 포함 되는지 여부를 확인할 수 없을 때 발생 합니다. 람다 식에 대한 자세한 내용은 [람다 식](../../cpp/lambda-expressions-in-cpp.md)을 참조하세요.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 대괄호 일부인 경우 특성 블록:

   1. 특성 블록에서 하나 이상의 특성을 제공 합니다.

   1. 특성 블록을 제거 합니다.

1. 대괄호를 사용 하면 람다 식의 일부인, 람다 식 구문이 규칙을 따르는지 있는지 확인 합니다.

   람다 식 구문에 대 한 자세한 내용은 참조 하세요. [람다 식 구문](../../cpp/lambda-expression-syntax.md)합니다.

## <a name="example"></a>예제

다음 예제에서는 C3409를 생성합니다.

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

## <a name="example"></a>예제

다음 예제에서는 람다 식 사용 하기 때문에 C3409를 생성 합니다 `mutable` 사양 하지만 매개 변수 목록을 제공 하지 않습니다. 컴파일러는 대괄호 특성 블록 또는 람다 식의 정의 포함 되는지 여부를 확인할 수 없습니다.

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>참고 항목

[attribute](../../windows/cpp-attributes-reference.md)<br/>
[람다 식](../../cpp/lambda-expressions-in-cpp.md)<br/>
[람다 식 구문](../../cpp/lambda-expression-syntax.md)