---
description: '자세한 정보: 컴파일러 오류 C3697'
title: 컴파일러 오류 C3697
ms.date: 11/04/2016
f1_keywords:
- C3697
helpviewer_keywords:
- C3697
ms.assetid: 2d3f63c4-b7f8-421d-a7a5-2bf17fd054f9
ms.openlocfilehash: 71b8a48cfe5be962c69dbc65730c1820d766f60d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228705"
---
# <a name="compiler-error-c3697"></a>컴파일러 오류 C3697

' 한정자 ': ' ^ '에이 한정자를 사용할 수 없습니다.

추적 핸들 (^)이 디자인 되지 않은 한정자에 적용 되었습니다.

다음 샘플에서는 C3697를 생성 합니다.

```cpp
// C3697.cpp
// compile with: /clr
using namespace System;
int main() {
   String ^__restrict s;   // C3697
   String ^ s2;   // OK
}
```
