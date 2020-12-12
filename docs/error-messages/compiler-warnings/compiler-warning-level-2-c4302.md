---
description: '자세한 정보: 컴파일러 경고 (수준 2) C4302'
title: 컴파일러 경고(수준 2) C4302
ms.date: 11/04/2016
f1_keywords:
- C4302
helpviewer_keywords:
- C4302
ms.assetid: f5e1c939-e134-4cca-ba1e-9b15a81549ae
ms.openlocfilehash: 0be91208d62c06882713d6b00358665f518103fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173560"
---
# <a name="compiler-warning-level-2-c4302"></a>컴파일러 경고(수준 2) C4302

' conversion ': ' type 1 '에서 ' type 2 ' (으)로 잘림

컴파일러가 더 큰 형식에서 더 작은 형식으로의 변환을 발견 했습니다. 정보가 손실 될 수 있습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4302를 생성 합니다.

```cpp
// C4302.cpp
// compile with: /W2
#pragma warning(default : 4302)
int main() {
   int i;
   char c = (char) &i;     // C4302
   short s = (short) &i;   // C4302
}
```
