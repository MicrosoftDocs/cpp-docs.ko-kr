---
description: '자세한 정보: 컴파일러 오류 C2086'
title: 컴파일러 오류 C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: b98b4ed3896b11d8df434935c1b539f76640f24c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252079"
---
# <a name="compiler-error-c2086"></a>컴파일러 오류 C2086

' identifier ': 재정의

식별자가 두 번 이상 정의 되었거나 후속 선언이 이전 선언과 다른 경우

C2086는 참조 된 c # 어셈블리에 대 한 증분 빌드의 결과일 수도 있습니다. 이 오류를 해결 하려면 c # 어셈블리를 다시 빌드합니다.

다음 샘플에서는 C2086를 생성 합니다.

```cpp
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```
