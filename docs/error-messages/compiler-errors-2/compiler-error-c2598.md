---
description: '자세한 정보: 컴파일러 오류 C2598'
title: 컴파일러 오류 C2598
ms.date: 11/04/2016
f1_keywords:
- C2598
helpviewer_keywords:
- C2598
ms.assetid: 40777c62-39ba-441e-b081-f49f94b43547
ms.openlocfilehash: 9ba2a37ee3acb841b340449e9a922ed98e3c9d24
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120089"
---
# <a name="compiler-error-c2598"></a>컴파일러 오류 C2598

링크 사양은 전역 범위에 있어야 합니다.

링크 지정자는 로컬 범위에서 선언 됩니다.

다음 샘플에서는 C2598를 생성 합니다.

```cpp
// C2598.cpp
// compile with: /c
void func() {
   extern "C" int func2();   // C2598
}

extern "C" int func( int i );
```
