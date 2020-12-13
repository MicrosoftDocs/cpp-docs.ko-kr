---
description: '자세한 정보: 컴파일러 오류 C2460'
title: 컴파일러 오류 C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: 6a6b521b356d4005906e97b085271369f2624c46
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341856"
---
# <a name="compiler-error-c2460"></a>컴파일러 오류 C2460

' identifier1 ': 정의 중인 ' identifier2 '를 사용 합니다.

클래스 또는 구조체 ( `identifier2` )는 자체의 멤버로 선언 됩니다 ( `identifier1` ). 클래스 및 구조체에 대 한 재귀 정의는 허용 되지 않습니다.

다음 샘플에서는 C2460를 생성 합니다.

```cpp
// C2460.cpp
class C {
   C aC;    // C2460
};
```

대신 클래스에서 포인터 참조를 사용 합니다.

```cpp
// C2460.cpp
class C {
   C * aC;    // OK
};
```
