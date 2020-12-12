---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4393'
title: 컴파일러 경고(수준 1) C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: e68829b7e41cbc1720ceb4dced374a53e97fe8d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212716"
---
# <a name="compiler-warning-level-1-c4393"></a>컴파일러 경고(수준 1) C4393

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
