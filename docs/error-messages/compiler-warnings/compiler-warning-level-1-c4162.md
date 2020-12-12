---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4162'
title: 컴파일러 경고 (수준 1) C4162
ms.date: 11/04/2016
f1_keywords:
- C4162
helpviewer_keywords:
- C4162
ms.assetid: 21ae3c92-501d-4689-ad7d-13753cb65eff
ms.openlocfilehash: 471d424329e2954ca96c860cabdc9774395b612b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267172"
---
# <a name="compiler-warning-level-1-c4162"></a>컴파일러 경고 (수준 1) C4162

' identifier ': C 링크가 있는 함수가 없습니다.

C 링크가 있는 함수가 선언 되었지만 찾을 수 없습니다.

이 경고를 해결 하려면 .c 파일 (C 컴파일러 호출)에서 컴파일합니다.  C + + 컴파일러를 호출 해야 하는 경우 함수 선언 앞에 extern "C"를 추가 합니다.

다음 샘플에서는 C4162를 생성 합니다.

```cpp
// C4162.cpp
// compile with: /c /W1
unsigned char _bittest(long* a, long b);
#pragma intrinsic (_bittest)   // C4162

int main() {
   bool bit;
   long num = 78002;
   bit = _bittest(&num, 5);
}
```

해결 방법:

```cpp
// C4162b.cpp
// compile with: /c
extern "C"
unsigned char _bittest(long* a, long b);
#pragma intrinsic (_bittest)

int main() {
   bool bit;
   long num = 78002;
   bit = _bittest(&num, 5);
}
```
