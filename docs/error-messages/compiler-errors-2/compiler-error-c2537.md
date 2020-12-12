---
description: '자세한 정보: 컴파일러 오류 C2537'
title: 컴파일러 오류 C2537
ms.date: 11/04/2016
f1_keywords:
- C2537
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
ms.openlocfilehash: 46603ded270b4702d4b7d4de97352547c5f503f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302038"
---
# <a name="compiler-error-c2537"></a>컴파일러 오류 C2537

' 지정자 ': 잘못 된 링크 사양입니다.

가능한 원인:

1. 링크 지정 자가 지원 되지 않습니다. "C" 링크 지정자만 지원 됩니다.

1. 오버 로드 된 함수 집합에서 둘 이상의 함수에 대해 "C" 링크를 지정 했습니다. 이것은 허용되지 않습니다.

다음 샘플에서는 C2537를 생성 합니다.

```cpp
// C2537.cpp
// compile with: /c
extern "c" void func();   // C2537
extern "C" void func2();   // OK
```
