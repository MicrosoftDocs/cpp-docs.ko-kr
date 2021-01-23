---
description: pragmaMicrosoft C/c + +에서 사용 되지 않는 지시문에 대해 자세히 알아보세요.
title: mapi pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.deprecated
helpviewer_keywords:
- deprecated pragma
- pragma, deprecated
no-loc:
- pragma
ms.openlocfilehash: 47e049f415b243a4c9959c7adc789f32f91de7ba
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98712910"
---
# <a name="deprecated-no-locpragma"></a>`deprecated` pragma

에서 **`deprecated`** pragma 함수, 형식 또는 다른 식별자가 이후 릴리스에서 더 이상 지원 되지 않거나 더 이상 사용 되지 않음을 나타낼 수 있습니다.

> [!NOTE]
> C + + 14 특성 및 Microsoft 한정자 또는를 사용 하는 경우에 대 한 지침에 대 한 자세한 내용은 `[[deprecated]]` `__declspec(deprecated)` **`deprecated`** pragma [c + +의 특성](../cpp/attributes.md)을 참조 하세요.

## <a name="syntax"></a>구문

> **`#pragma deprecated(`***identifier1* [ **`,`** *identifier2* ]**`)`**

## <a name="remarks"></a>설명

컴파일러가에서 지정 된 식별자를 발견 하면 **`deprecated`** pragma 컴파일러 경고 [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)이 발생 합니다.

매크로 이름을 사용하지 않을 수 있습니다. 매크로 이름을 따옴표로 묶지 않으면 매크로 확장이 발생합니다.

는 **`deprecated`** pragma 일치 하는 모든 식별자에 대해 작동 하 고 서명을 고려 하지 않으므로 오버 로드 된 함수의 사용 중단 특정 버전을 사용 하는 것이 가장 좋은 옵션이 아닙니다. 범위에 있는 일치 하는 함수 이름은 모두 경고를 트리거합니다.

가능 하면 대신 c + + 14 특성을 사용 하는 것이 좋습니다 `[[deprecated]]` **`deprecated`** pragma . Microsoft 전용 [`__declspec(deprecated)`](../cpp/deprecated-cpp.md) 선언 한정자는가 아닌 대부분의 경우에도 더 적합 합니다 **`deprecated`** pragma . `[[deprecated]]`특성 및 `__declspec(deprecated)` 한정자를 사용 하면 오버 로드 된 함수의 특정 형식에 대해 사용 되지 않는 상태를 지정할 수 있습니다. 진단 경고는 특성이 나 한정자가 적용 되는 특정 오버 로드 된 함수에 대 한 참조에만 표시 됩니다.

## <a name="example"></a>예제

```cpp
// pragma_directive_deprecated.cpp
// compile with: /W3
#include <stdio.h>
void func1(void) {
}

void func2(void) {
}

int main() {
   func1();
   func2();
   #pragma deprecated(func1, func2)
   func1();   // C4995
   func2();   // C4995
}
```

다음 샘플에서는 클래스를 사용하지 않는 방법을 보여 줍니다.

```cpp
// pragma_directive_deprecated2.cpp
// compile with: /W3
#pragma deprecated(X)
class X {  // C4995
public:
   void f(){}
};

int main() {
   X x;   // C4995
}
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
