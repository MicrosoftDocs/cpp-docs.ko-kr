---
description: '자세한 정보: 컴파일러 오류 C2473'
title: 컴파일러 오류 C2473
ms.date: 11/04/2016
f1_keywords:
- C2473
helpviewer_keywords:
- C2473
ms.assetid: 6bb7dbf5-b198-490f-860e-fd64d0c2a284
ms.openlocfilehash: c81e1329e17c03b3bd8f857d2f8ceddcc1a9f264
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164460"
---
# <a name="compiler-error-c2473"></a>컴파일러 오류 C2473

'identifier': 함수 정의로 보이지만 매개 변수 목록이 없습니다.

컴파일러가 매개 변수 목록 없이 함수처럼 보이는 항목을 발견했습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2473을 생성합니다.

```cpp
// C2473.cpp
// compile with: /clr /c
class A {
   int i {}   // C2473
};

class B {
   int i() {}   // OK
};
```
