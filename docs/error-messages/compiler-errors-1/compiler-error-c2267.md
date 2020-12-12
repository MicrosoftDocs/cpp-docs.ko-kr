---
description: '자세한 정보: 컴파일러 오류 C2267'
title: 컴파일러 오류 C2267
ms.date: 11/04/2016
f1_keywords:
- C2267
helpviewer_keywords:
- C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
ms.openlocfilehash: df69073cbb1956033cf7d028c56e13018e4bbcf4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328406"
---
# <a name="compiler-error-c2267"></a>컴파일러 오류 C2267

' function ': 블록 범위를 사용 하는 정적 함수가 잘못 되었습니다.

로컬 함수가 선언 됩니다 **`static`** . 정적 함수는 전역 범위를 가져야 합니다.

다음 샘플에서는 C2267를 생성 합니다.

```cpp
// C2267.cpp
static int func2();   // OK
int main() {
    static int func1();   // C2267
}
```
