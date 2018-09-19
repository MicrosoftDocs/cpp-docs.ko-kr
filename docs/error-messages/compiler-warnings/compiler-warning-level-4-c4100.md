---
title: 컴파일러 경고 (수준 4) C4100 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4100
dev_langs:
- C++
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6ad1b8bab287f4c16b00781e90351bbb204aa91
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099468"
---
# <a name="compiler-warning-level-4-c4100"></a>컴파일러 경고(수준 4) C4100

'identifier': 참조 되지 않은 정식 매개 변수

형식 매개 변수는 함수 본문에서 참조 되지 않습니다. 참조 되지 않은 매개 변수가 무시 됩니다.

코드에서 소멸자를 호출할 때 C4100 발급할 수도 있습니다는 참조 되지 않는 기본 형식의 매개 변수입니다.  Visual c + + 컴파일러의 제한 됩니다.

다음 샘플에서는 C4100 오류가 생성 됩니다.

```
// C4100.cpp
// compile with: /W4
void func(int i) {   // C4100, delete the unreferenced parameter to
                     //resolve the warning
   // i;   // or, add a reference like this
}

int main()
{
   func(1);
}
```