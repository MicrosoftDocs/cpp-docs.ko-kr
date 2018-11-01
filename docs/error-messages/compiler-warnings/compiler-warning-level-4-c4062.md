---
title: 컴파일러 경고(수준 4) C4062
ms.date: 11/04/2016
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: 6a7129f71eebb33e7bde333dfd90ed4ca173d44c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602646"
---
# <a name="compiler-warning-level-4-c4062"></a>컴파일러 경고(수준 4) C4062

열거형 'enumeration'의 switch에 있는 'identifier' 열거자가 처리되지 않습니다.

열거와 연결된 처리기가 `switch` 문에 없고, **기본** 레이블이 없습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4062를 생성합니다.

```
// C4062.cpp
// compile with: /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
      break;   // no default label
   }   // C4062, enumerate 'c' not handled
}

int main() {
}
```