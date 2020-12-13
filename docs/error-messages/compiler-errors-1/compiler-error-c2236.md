---
description: '자세한 정보: 컴파일러 오류 C2236'
title: 컴파일러 오류 C2236
ms.date: 11/04/2016
f1_keywords:
- C2236
helpviewer_keywords:
- C2236
ms.assetid: 0b6771a7-a783-4729-9c3d-7a3339c432cc
ms.openlocfilehash: 91b04cad6be02a3a50a21af9ef3397fb17d9c43b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338738"
---
# <a name="compiler-error-c2236"></a>컴파일러 오류 C2236

예기치 않은 토큰 'identifier'입니다. ';'이 없습니다.

식별자가 이미 형식으로 정의되었으며 사용자 정의 형식으로 재정의할 수 없습니다.

다음 샘플에서는 C2236을 생성합니다.

```cpp
// C2236.cpp
// compile with: /c
int class A {};  // C2236 "int class" is unexpected
int i;
class B {};
```
