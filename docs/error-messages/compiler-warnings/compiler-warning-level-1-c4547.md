---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4547'
title: 컴파일러 경고(수준 1) C4547
ms.date: 11/04/2016
f1_keywords:
- C4547
helpviewer_keywords:
- C4547
ms.assetid: 3edf1c2e-c0d5-444d-ae83-44a7cce24bb2
ms.openlocfilehash: 59295f7f8a0a71e638a28ddc3a316e9c020cc652
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266015"
---
# <a name="compiler-warning-level-1-c4547"></a>컴파일러 경고(수준 1) C4547

' operator ': 쉼표 앞의 연산자는 적용 되지 않습니다. 부작용이 있는 연산자가 필요 합니다.

컴파일러가 잘못 된 형식의 쉼표 식을 발견 했습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)을 참조하세요.

다음 샘플에서는 C4547를 생성 합니다.

```cpp
// C4547.cpp
// compile with: /W1
#pragma warning (default : 4547)
int i = 0;
int j = 1;
int main() {
   int l = (i != i,0);   // C4547
   // try the following line instead
   // int l = (i != i);
   // or
   // int l = ((void)(i != i),0);
}
```
