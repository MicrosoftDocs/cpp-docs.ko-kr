---
title: 컴파일러 오류 C2197 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2197
dev_langs:
- C++
helpviewer_keywords:
- C2197
ms.assetid: 6dd5a6ec-bc80-41b9-a4ac-46f80eaca42d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb8e13e21cbba3b6cbf6a4bd84a835270d7fee2c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036820"
---
# <a name="compiler-error-c2197"></a>컴파일러 오류 C2197

'function': 호출에 매개 변수가 너무 많습니다.

컴파일러가 함수 호출 매개 변수를 너무 많이 발견했거나 잘못된 함수 선언을 발견했습니다.

다음 샘플에서는 C2197을 생성합니다.

```
// C2197.c
// compile with: /Za /c
void func( int );
int main() {
   func( 1, 2 );   // C2197 two actual parameters
   func( 2 );   // OK
}
```