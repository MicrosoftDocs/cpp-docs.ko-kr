---
description: '자세한 정보: 컴파일러 오류 C2142'
title: 컴파일러 오류 C2142
ms.date: 11/04/2016
f1_keywords:
- C2142
helpviewer_keywords:
- C2142
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
ms.openlocfilehash: 65bd189fe99bb54549e458b093b72d8e47b840a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235530"
---
# <a name="compiler-error-c2142"></a>컴파일러 오류 C2142

함수 선언이 다릅니다. 변수 매개 변수는 그 중 하나에만 지정 됩니다.

함수의 한 선언에는 가변 매개 변수 목록이 포함 됩니다. 다른 선언은 그렇지 않습니다. ANSI C ([/za](../../build/reference/za-ze-disable-language-extensions.md))만 해당 합니다.

다음 샘플에서는 C2142를 생성 합니다.

```c
// C2142.c
// compile with: /Za /c
void func();
void func( int, ... );   // C2142
void func2( int, ... );   // OK
```
