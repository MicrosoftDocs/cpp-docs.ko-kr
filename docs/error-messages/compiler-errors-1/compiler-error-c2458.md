---
description: '자세한 정보: 컴파일러 오류 C2458'
title: 컴파일러 오류 C2458
ms.date: 11/04/2016
f1_keywords:
- C2458
helpviewer_keywords:
- C2458
ms.assetid: ed21901f-1067-42f5-b275-19b480decf5c
ms.openlocfilehash: 7f705511c14da19b125868c1b34d907d6b5f220e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262856"
---
# <a name="compiler-error-c2458"></a>컴파일러 오류 C2458

' identifier ': 정의 내에서 재정의 합니다.

클래스, 구조체, 공용 구조체 또는 열거형은 자체 선언에서 다시 정의 됩니다.

다음 샘플에서는 C2458를 생성 합니다.

```cpp
// C2458.cpp
class C {
   enum i { C };   // C2458
};
```
