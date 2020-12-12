---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4566'
title: 컴파일러 경고(수준 1) C4566
ms.date: 11/04/2016
f1_keywords:
- C4566
helpviewer_keywords:
- C4566
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
ms.openlocfilehash: 2e0d1f5b80a42d58f2866109957e466d3ab36cc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332247"
---
# <a name="compiler-warning-level-1-c4566"></a>컴파일러 경고(수준 1) C4566

유니버설 문자 이름 ' char '로 표시 되는 문자는 현재 코드 페이지 (페이지)에서 표현할 수 없습니다.

현재 ANSI 코드 페이지에 모든 유니코드 문자를 표시할 수 있는 것은 아닙니다.

좁은 문자열 (1 바이트 문자)은 멀티 바이트 문자로 변환 되지만 와이드 문자열 (2 바이트 문자)는 멀티 바이트 문자로 변환 됩니다.

다음 샘플에서는 C4566를 생성 합니다.

```cpp
// C4566.cpp
// compile with: /W1
int main() {
   char c1 = '\u03a0';   // C4566
   char c2 = '\u0642';   // C4566

   wchar_t c3 = L'\u03a0';   // OK
   wchar_t c4 = L'\u0642';   // OK
}
```
