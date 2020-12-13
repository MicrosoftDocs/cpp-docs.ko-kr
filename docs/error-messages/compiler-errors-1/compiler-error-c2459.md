---
description: '자세한 정보: 컴파일러 오류 C2459'
title: 컴파일러 오류 C2459
ms.date: 11/04/2016
f1_keywords:
- C2459
helpviewer_keywords:
- C2459
ms.assetid: 81e29f4c-5b60-40fb-9557-1cdc630d77e8
ms.openlocfilehash: 35cd97b93a7095aedc0015e2e7d9910172425263
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341869"
---
# <a name="compiler-error-c2459"></a>컴파일러 오류 C2459

' identifier ':을 (를) 정의 하는 중입니다. 익명 멤버로 추가할 수 없습니다.

클래스, 구조체 또는 공용 구조체가 익명 공용 구조체의 멤버에 의해 자체 범위에서 다시 정의 됩니다.

다음 샘플에서는 C2459를 생성 합니다.

```cpp
// C2459.cpp
// compile with: /c
class C {
   union { int C; };   // C2459
   union { int D; };
};
```
