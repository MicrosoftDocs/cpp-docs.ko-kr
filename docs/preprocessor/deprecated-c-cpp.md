---
title: deprecated pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 5694c5175ff23952c601884243b428a842278b7d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446481"
---
# <a name="deprecated-pragma"></a>deprecated pragma

**사용 되지 않는** pragma를 사용 하면 함수, 형식 또는 다른 식별자가 이후 릴리스에서 더 이상 지원 되지 않거나 더 이상 사용 되지 않음을 나타낼 수 있습니다.

> [!NOTE]
> C + + 14 `[[deprecated]]` 특성에 대 한 자세한 내용과 Microsoft `__declspec(deprecated)` 한정자 또는 사용 **되지 않는** pragma 대신 해당 특성을 사용 하는 경우에 대 한 지침은 [의 C++특성 ](../cpp/attributes.md)을 참조 하세요.

## <a name="syntax"></a>구문

> **#pragma 사용 되지 않음 (** *identifier1* [ **,** *identifier2* ] **)**

## <a name="remarks"></a>설명

컴파일러가 **사용 되지 않는** pragma로 지정 된 식별자를 발견 하면 컴파일러 경고 [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)이 발생 합니다.

매크로 이름을 사용하지 않을 수 있습니다. 매크로 이름을 따옴표로 감싸면 매크로가 적용됩니다.

**사용 되지** 않는 pragma는 일치 하는 모든 식별자에 대해 작동 하 고 서명을 고려 하지 않으므로 오버 로드 된 함수의 사용 중단 특정 버전을 사용 하는 것이 가장 적합 한 옵션이 아닙니다. 범위 안에 함수 이름이 일치한다면 경고가 발생합니다.

가능 하면 사용 **되지 않는** Pragma 대신 c + + 14 `[[deprecated]]` 특성을 사용 하는 것이 좋습니다. Microsoft 전용 [__declspec (사용 되지 않음)](../cpp/deprecated-cpp.md) 선언 한정자는 **사용 되지 않는** pragma 보다 많은 경우에도 더 적합 합니다. `[[deprecated]]` attribute 및 `__declspec(deprecated)` 한정자를 사용 하면 오버 로드 된 특정 형식의 오버 로드 된 함수에 대해 사용 되지 않는 상태를 지정할 수 있습니다. 진단경고는 특성 또는 한정자가 적용되는 특정 오버로드 된 함수에 대한 참조에만 나타납니다.

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

다음 샘플에서는 클래스X를 사용하지 말것을 권장하는 방법을 보여 줍니다.

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

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)