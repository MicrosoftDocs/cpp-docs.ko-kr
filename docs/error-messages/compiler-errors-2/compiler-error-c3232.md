---
description: '자세한 정보: 컴파일러 오류 C3232'
title: 컴파일러 오류 C3232
ms.date: 11/04/2016
f1_keywords:
- C3232
helpviewer_keywords:
- C3232
ms.assetid: 3119b3a9-0eff-4a3f-b805-e4d160af9e39
ms.openlocfilehash: 180af73cc76afdca9d21c168e925bc1755cd88a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312009"
---
# <a name="compiler-error-c3232"></a>컴파일러 오류 C3232

'param': 정규화된 이름에는 제네릭 형식 매개 변수를 사용할 수 없습니다.

제네릭 형식 매개 변수가 잘못 사용되었습니다.

다음 샘플에서는 C3232를 생성합니다.

```cpp
// C3232.cpp
// compile with: /clr
generic <class T>
ref class C {
   typename T::TYPE t;   // C3232
};
```
