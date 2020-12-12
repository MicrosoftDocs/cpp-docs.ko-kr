---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4548'
title: 컴파일러 경고(수준 1) C4548
ms.date: 11/04/2016
f1_keywords:
- C4548
helpviewer_keywords:
- C4548
ms.assetid: 2cee817e-e463-4d90-bbd2-de120d48c101
ms.openlocfilehash: 7c0f88f6516b1069fa9ef13e56c5ca043f627820
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266002"
---
# <a name="compiler-warning-level-1-c4548"></a>컴파일러 경고(수준 1) C4548

쉼표 앞의 식은 의미 없는 식입니다. 파생 작업이 있는 식이어야 합니다.

컴파일러가 잘못 된 형식의 쉼표 식을 발견 했습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)을 참조하세요.

다음 샘플에서는 C4548를 생성 합니다.

```cpp
// C4548.cpp
// compile with: /W1
#pragma warning (default : 4548)
int main()
{
   int i = 0, k = 0;

   if ( i, k )   // C4548
   // try the following line instead
   // if ( i = 0, k )
      i++;
}
```
