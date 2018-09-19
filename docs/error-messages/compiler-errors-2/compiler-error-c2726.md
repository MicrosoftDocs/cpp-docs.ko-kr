---
title: 컴파일러 오류 C2726 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2726
dev_langs:
- C++
helpviewer_keywords:
- C2726
ms.assetid: f0191bb7-c175-450b-bf09-a3213db96d09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e421839e75bcc570578d7c37eecc8ab076321d7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051275"
---
# <a name="compiler-error-c2726"></a>컴파일러 오류 C2726

'gcnew'는 WinRT 또는 관리되는 형식의 개체를 만드는 데만 사용할 수 있습니다.

가비지 수집된 힙에 네이티브 형식의 인스턴스를 만들 수 없습니다.

다음 샘플에서는 C2726 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```
// C2726.cpp
// compile with: /clr
using namespace System;
class U {};
ref class V {};
value class W {};

int main() {
   U* pU = gcnew U;    // C2726
   U* pU2 = new U;   // OK
   V^ p2 = gcnew V;   // OK
   W p3;   // OK

}
```
