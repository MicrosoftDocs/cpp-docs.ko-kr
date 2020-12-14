---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4254'
title: 컴파일러 경고(수준 4) C4254
ms.date: 11/04/2016
f1_keywords:
- c4254
helpviewer_keywords:
- C4254
ms.assetid: c7dcef24-d535-4c98-bb41-fc3d2b88fd11
ms.openlocfilehash: 112a8c4af016b15f6a5ec4c6e138381a8ee32405
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294706"
---
# <a name="compiler-warning-level-4-c4254"></a>컴파일러 경고(수준 4) C4254

' operator ': ' type1 '에서 ' type2 ' (으)로 변환 하 여 데이터가 손실 될 수 있습니다.

더 큰 비트 필드가 더 작은 비트 필드에 할당 되었습니다. 데이터가 손실 될 수 있습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4254를 생성 합니다.

```cpp
// C4254.cpp
// compile with: /W4
#pragma warning(default: 4254)

struct X {
   int a : 20;
   int b : 12;
};

int main() {
   X *x = new X();
   x->b = 10;
   x->a = 4;
   x->a = x->b;    // OK
   x->b = x->a;    // C4254
};
```
