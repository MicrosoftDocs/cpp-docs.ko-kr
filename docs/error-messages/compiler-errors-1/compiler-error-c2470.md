---
description: '자세한 정보: 컴파일러 오류 C2470'
title: 컴파일러 오류 C2470
ms.date: 11/04/2016
f1_keywords:
- C2470
helpviewer_keywords:
- C2470
ms.assetid: e17d2cb8-b84c-447c-976a-625f0c96f3fe
ms.openlocfilehash: 90a57f02022044aca7b4062ea287eae213c26f74
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164512"
---
# <a name="compiler-error-c2470"></a>컴파일러 오류 C2470

' function ': 함수 정의 처럼 보이지만 매개 변수 목록이 없습니다. 명백한 본문을 건너뛰고 있습니다.

함수 정의에 인수 목록이 없습니다.

다음 샘플에서는 C2470를 생성 합니다.

```cpp
// C2470.cpp
int MyFunc {};  // C2470
void MyFunc2() {};  //OK

int main(){
   MyFunc();
   MyFunc2();
}
```
