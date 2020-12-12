---
description: '자세한 정보: 컴파일러 오류 C2375'
title: 컴파일러 오류 C2375
ms.date: 11/04/2016
f1_keywords:
- C2375
helpviewer_keywords:
- C2375
ms.assetid: 193c5e8b-1b20-4928-8a02-8c1cddaf2a26
ms.openlocfilehash: 187188caa851191c44280e24d9321ea3cb24f9f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174769"
---
# <a name="compiler-error-c2375"></a>컴파일러 오류 C2375

'function': 재정의. 링크가 다릅니다.

함수가 다른 링크 지정자를 사용하여 이미 선언되었습니다.

다음 샘플에서는 C2375를 생성합니다.

```cpp
// C2375.cpp
// compile with: /Za /c
extern void func( void );
static void func( void );   // C2375
static void func2( void );   // OK
```
