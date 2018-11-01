---
title: 컴파일러 오류 C3891
ms.date: 11/04/2016
f1_keywords:
- C3891
helpviewer_keywords:
- C3891
ms.assetid: 6e1a9458-97f5-4580-bc0f-aa97a1bfd20d
ms.openlocfilehash: 67d12984a32998c244bcd04f99a5f2200a192974
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524568"
---
# <a name="compiler-error-c3891"></a>컴파일러 오류 C3891

'var': 리터럴 데이터 멤버는 l-value로 사용할 수 없습니다

A [리터럴](../../windows/literal-cpp-component-extensions.md) 변수는 const 및 선언에서 초기화 한 후 해당 값을 변경할 수 없습니다.

다음 샘플에서는 C3891 오류가 생성 됩니다.

```
// C3891.cpp
// compile with: /clr
ref struct Y1 {
   literal int staticConst = 9;
};

int main() {
   Y1::staticConst = 0;   // C3891
}
```