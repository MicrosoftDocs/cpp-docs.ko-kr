---
description: '자세한 정보: 컴파일러 오류 C3873'
title: 컴파일러 오류 C3873
ms.date: 11/04/2016
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
ms.openlocfilehash: 7ca1346d2a1f22e1aa8bd2a7197daa41d8b416aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222725"
---
# <a name="compiler-error-c3873"></a>컴파일러 오류 C3873

'char': 이 문자는 식별자의 첫 문자로 사용할 수 없습니다.

C++ 컴파일러는 식별자에서 허용되는 문자에 대한 C++11 표준을 따릅니다. 특정 범위의 문자와 유니버설 문자 이름만 식별자에서 허용됩니다. 식별자의 시작 문자에는 추가 제한이 적용됩니다. 자세한 내용 및 허용되는 문자 목록과 유니버설 문자 이름 범위는 [Identifiers](../../cpp/identifiers-cpp.md)를 참조하세요.

식별자에서 허용되는 문자의 범위는 C++/CLI 코드를 컴파일하는 경우보다 덜 제한적입니다. /clr을 사용하여 컴파일된 코드의 식별자는  [Standard ECMA-335: Common Language Infrastructure(CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm)를 준수해야 합니다.

다음 샘플에서는 C3873을 생성합니다.

```cpp
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```
