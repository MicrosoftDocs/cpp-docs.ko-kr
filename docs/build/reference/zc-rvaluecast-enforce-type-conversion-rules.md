---
description: '자세한 정보:/Zc: rvalueCast (형식 변환 규칙 적용)'
title: /Zc:rvalueCast(형식 변환 규칙 적용)
ms.date: 02/18/2020
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
ms.openlocfilehash: f9739f16b12e5e0335f17bb5a56ed1e4aa265e9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269148"
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast(형식 변환 규칙 적용)

**`/Zc:rvalueCast`** 옵션이 지정 된 경우 컴파일러는 캐스트 작업의 결과로 rvalue 참조 형식을 올바르게 식별 합니다. 해당 동작은 c + + 11 표준을 따릅니다. 옵션이 지정 되지 않은 경우 컴파일러 동작은 Visual Studio 2012와 동일 합니다.

## <a name="syntax"></a>구문

> **`/Zc:rvalueCast`**\
> **`/Zc:rvalueCast-`**

## <a name="remarks"></a>설명

**`/Zc:rvalueCast`** 이 지정 된 경우 컴파일러는 c + + 11 표준의 섹션 5.4을 따르고 비 참조 형식을 반환 하는 캐스트 식과 rvalue 형식으로 비 함수 형식에 대 한 rvalue 참조를 결과로 반환 하는 캐스트 식만 처리 합니다. 기본적으로 또는 **`/Zc:rvalueCast-`** 가 지정 된 경우 컴파일러는 비준수로 간주 하 고 rvalue 참조를 결과로 반환 하는 모든 캐스트 식을 rvalue로 처리 합니다. 규칙을 준수 하 고 캐스트 사용 시 발생 하는 오류를 없애려면를 사용 하는 것이 좋습니다 **`/Zc:rvalueCast`** .

기본적으로 **`/Zc:rvalueCast`** 는 off ( **`/Zc:rvalueCast-`** )입니다. [/Permissive-](permissive-standards-conformance.md) 컴파일러 옵션은이 옵션을 암시적으로 설정 하지만을 사용 하 여 재정의할 수 있습니다 **`/Zc:rvalueCast-`** .

**`/Zc:rvalueCast`** Rvalue 참조 형식을 사용 하는 함수에 대 한 인수로 캐스트 식을 전달 하는 경우를 사용 합니다. 컴파일러가 캐스트 식의 형식을 잘못 결정 하면 기본 동작으로 인해 컴파일러 오류가 [c 2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) 됩니다. 이 예제에서는가 지정 되지 않은 경우 올바른 코드의 컴파일러 오류를 보여 줍니다 **`/Zc:rvalueCast`** .

```cpp
// Test of /Zc:rvalueCast
// compile by using:
// cl /c /Zc:rvalueCast- make_thing.cpp
// cl /c /Zc:rvalueCast make_thing.cpp

#include <utility>

template <typename T>
struct Thing {
   // Construct a Thing by using two rvalue reference parameters
   Thing(T&& t1, T&& t2)
      : thing1(t1), thing2(t2) {}

   T& thing1;
   T& thing2;
};

// Create a Thing, using move semantics if possible
template <typename T>
Thing<T> make_thing(T&& t1, T&& t2)
{
   return (Thing<T>(std::forward<T>(t1), std::forward<T>(t2)));
}

struct Test1 {
   long a;
   long b;

   Thing<long> test() {
      // Use identity casts to create rvalues as arguments
      return make_thing(static_cast<long>(a), static_cast<long>(b));
   }
};
```

보고하지 않는 것이 적절한 경우 기본 컴파일러 동작이 오류 C2102를 보고하지 않을 수도 있습니다. 이 예제에서는가 지정 되지 않은 경우 id 캐스트를 통해 생성 된 rvalue의 주소를 사용 하는 경우 컴파일러에서 오류를 보고 하지 않습니다 **`/Zc:rvalueCast`** .

```cpp
int main() {
   int a = 1;
   int *p = &a;   // Okay, take address of lvalue
                  // Identity cast creates rvalue from lvalue;
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value
}
```

Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **언어** 속성 페이지를 선택 합니다.

1. **형식 변환 규칙 적용** 속성을 또는로 설정 합니다 **`/Zc:rvalueCast`** **`/Zc:rvalueCast-`** . **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

## <a name="see-also"></a>참고 항목

[/Zc(규칙)](zc-conformance.md)
