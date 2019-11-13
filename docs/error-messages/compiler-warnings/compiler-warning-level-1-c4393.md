---
title: 컴파일러 경고 (수준 1) C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: 92cb9a063a2f6e4660c3f84516527c1417c55e46
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966145"
---
# <a name="compiler-warning-level-1-c4393"></a>컴파일러 경고 (수준 1) C4393

' var ': const는 리터럴 데이터 멤버에는 영향을 주지 않습니다. 무시

[리터럴](../../extensions/literal-cpp-component-extensions.md) 데이터 멤버도 const로 지정 되었습니다.  리터럴 데이터 멤버는 const를 암시 하므로 선언에 const를 추가할 필요가 없습니다.

다음 샘플에서는 C4393를 생성 합니다.

```cpp
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```