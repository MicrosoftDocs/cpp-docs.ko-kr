---
description: '자세한 정보: 컴파일러 오류 C2800'
title: 컴파일러 오류 C2800
ms.date: 11/04/2016
f1_keywords:
- C2800
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
ms.openlocfilehash: 7adcb8e24bd7b3f3941260a9cceaa5157334ae8d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297507"
---
# <a name="compiler-error-c2800"></a>컴파일러 오류 C2800

' operator operator '를 오버 로드할 수 없습니다.

다음 연산자는 오버 로드할 수 없습니다. 클래스 멤버 액세스 ( `.` ), 멤버 포인터 ( `.*` ), 범위 확인 ( `::` ), 조건식 ( `? :` ) 및 **`sizeof`** .

다음 샘플에서는 C2800를 생성 합니다.

```cpp
// C2800.cpp
// compile with: /c
class C {
   operator:: ();   // C2800
};
```
