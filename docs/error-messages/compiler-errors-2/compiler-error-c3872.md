---
title: 컴파일러 오류 C3872 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3872
dev_langs:
- C++
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec6450dca0faa86f3cf27452eff6df9851742d4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018836"
---
# <a name="compiler-error-c3872"></a>컴파일러 오류 C3872

'char': 식별자에는 이 문자를 사용할 수 없습니다.

C++ 컴파일러는 식별자에서 허용되는 문자에 대한 C++11 표준을 따릅니다. 특정 범위의 문자와 유니버설 문자 이름만 식별자에서 허용됩니다. 식별자의 시작 문자에는 추가 제한이 적용됩니다. 자세한 내용 및 허용되는 문자 목록과 유니버설 문자 이름 범위는 [Identifiers](../../cpp/identifiers-cpp.md)를 참조하세요.

식별자에서 허용되는 문자의 범위는 C++/CLI 코드를 컴파일하는 경우보다 덜 제한적입니다. /clr을 사용하여 컴파일된 코드의 식별자는  [Standard ECMA-335: Common Language Infrastructure(CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)를 준수해야 합니다.

다음 샘플에서는 C3872를 생성합니다.

```
// C3872.cpp
int main() {
   int abc_\u0040;   // C3872, U+0040 is in base char set
   int abc_\u3001;   // C3872, U+3001 is not in allowed range
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range
}
```