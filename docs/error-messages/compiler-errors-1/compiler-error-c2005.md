---
description: '자세한 정보: 컴파일러 오류 C2005'
title: 컴파일러 오류 C2005
ms.date: 11/04/2016
f1_keywords:
- C2005
helpviewer_keywords:
- C2005
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
ms.openlocfilehash: 80ed80433d2e227b4c904d6ce4a68318feb98b05
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298580"
---
# <a name="compiler-error-c2005"></a>컴파일러 오류 C2005

\#줄에 줄 번호가 있어야 하는데 ' token '이 있습니다.

`#line`지시문 뒤에는 줄 번호가와 야 합니다.

다음 샘플에서는 C2005를 생성 합니다.

```cpp
// C2005.cpp
int main() {
   int i = 0;
   #line i   // C2005
}
```

해결 방법:

```cpp
// C2005b.cpp
int main() {
   int i = 0;
   #line 0
}
```
