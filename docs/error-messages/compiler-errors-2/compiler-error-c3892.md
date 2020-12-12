---
description: '자세한 정보: 컴파일러 오류 C3892'
title: 컴파일러 오류 C3892
ms.date: 11/04/2016
f1_keywords:
- C3892
helpviewer_keywords:
- C3892
ms.assetid: 83fff42c-ea48-442f-bc2e-b33a6b99d890
ms.openlocfilehash: 1fe2692e594debebdaf3493414d0e6136c9403a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274270"
---
# <a name="compiler-error-c3892"></a>컴파일러 오류 C3892

' var ': const 인 변수에 할당할 수 없습니다.

Const 변수를 선언 하 고 초기화 한 후에는 변경할 수 없습니다.

다음 샘플에서는 C3892를 생성 합니다.

```cpp
// C3892.cpp
// compile with: /clr
ref struct Y1 {
   static const int staticConst = 9;
};

int main() {
   Y1::staticConst = 0;   // C3892
}
```
