---
title: 컴파일러 오류 C3873 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83580d8202dada0b650b1703dcadf9b99e6771d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072812"
---
# <a name="compiler-error-c3873"></a>컴파일러 오류 C3873

'char': 이 문자는 식별자의 첫 문자로 사용할 수 없습니다.

C++ 컴파일러는 식별자에서 허용되는 문자에 대한 C++11 표준을 따릅니다. 특정 범위의 문자와 유니버설 문자 이름만 식별자에서 허용됩니다. 식별자의 시작 문자에는 추가 제한이 적용됩니다. 자세한 내용 및 허용되는 문자 목록과 유니버설 문자 이름 범위는 [Identifiers](../../cpp/identifiers-cpp.md)를 참조하세요.

식별자에서 허용되는 문자의 범위는 C++/CLI 코드를 컴파일하는 경우보다 덜 제한적입니다. /clr을 사용하여 컴파일된 코드의 식별자는  [Standard ECMA-335: Common Language Infrastructure(CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)를 준수해야 합니다.

다음 샘플에서는 C3873을 생성합니다.

```
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```