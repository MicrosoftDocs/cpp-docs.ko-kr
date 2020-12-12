---
description: '자세한 정보: 컴파일러 오류 C2087'
title: 컴파일러 오류 C2087
ms.date: 11/04/2016
f1_keywords:
- C2087
helpviewer_keywords:
- C2087
ms.assetid: 89761e83-415a-4468-a4c6-b6dedfd1dd6a
ms.openlocfilehash: 98e54a8df8f06230f1adca1cb6d2f23f80acff8e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252040"
---
# <a name="compiler-error-c2087"></a>컴파일러 오류 C2087

' identifier ': 첨자가 없습니다.

여러 첨자가 있는 배열의 정의에 1 보다 큰 차원에 대 한 첨자 값이 누락 되었습니다.

다음 샘플에서는 C2087를 생성 합니다.

```cpp
// C2087.cpp
int main() {
   char a[10][];   // C2087
}
```

해결 방법:

```cpp
// C2087b.cpp
int main() {
   char b[4][5];
}
```
