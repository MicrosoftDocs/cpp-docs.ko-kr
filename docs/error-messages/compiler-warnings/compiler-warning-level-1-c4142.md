---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4142'
title: 컴파일러 경고 (수준 1) C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: d82403d79310d577cd45fe835cd486719ea0fdc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115731"
---
# <a name="compiler-warning-level-1-c4142"></a>컴파일러 경고 (수준 1) C4142

형식 재정의 무해

형식은 생성 된 코드에 영향을 주지 않는 방식으로 다시 정의 됩니다.

다음과 같은 가능한 원인을 확인하여 수정하세요.

- 파생 클래스의 멤버 함수는 기본 클래스의 해당 멤버 함수와 다른 반환 형식을 갖습니다.

- 명령을 사용 하 여 정의 된 형식은 **`typedef`** 다른 구문을 사용 하 여 다시 정의 됩니다.

다음 샘플에서는 C4142를 생성 합니다.

```c
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```
