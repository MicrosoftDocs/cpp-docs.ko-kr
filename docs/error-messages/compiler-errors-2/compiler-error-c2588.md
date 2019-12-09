---
title: 컴파일러 오류 C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: f1f73e2585606e7e86213607a96ef713345419c1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755410"
---
# <a name="compiler-error-c2588"></a>컴파일러 오류 C2588

':: ~ identifier ': 전역 소멸자가 잘못 되었습니다.

소멸자는 클래스, 구조체 또는 공용 구조체가 아닌 다른 항목에 대해 정의 됩니다. 이는 허용되지 않습니다.

이 오류는 범위 확인 (`::`) 연산자의 왼쪽에 클래스, 구조체 또는 공용 구조체 이름이 누락 되었기 때문에 발생할 수 있습니다.

다음 샘플에서는 C2588를 생성 합니다.

```cpp
// C2588.cpp
~F();   // C2588
```
