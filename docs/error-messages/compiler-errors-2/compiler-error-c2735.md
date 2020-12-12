---
description: '자세한 정보: 컴파일러 오류 C2735'
title: 컴파일러 오류 C2735
ms.date: 11/04/2016
f1_keywords:
- C2735
helpviewer_keywords:
- C2735
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
ms.openlocfilehash: 75596e403c118d17ee286a579a347f6793c30bbd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123151"
---
# <a name="compiler-error-c2735"></a>컴파일러 오류 C2735

' keyword ' 키워드는 정식 매개 변수 형식 지정자에 사용할 수 없습니다.

이 컨텍스트에서는 키워드를 사용할 수 없습니다.

다음 샘플에서는 C2735를 생성 합니다.

```cpp
// C2735.cpp
void f(inline int){}   // C2735
```
