---
title: 컴파일러 오류 C2489 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2489
dev_langs:
- C++
helpviewer_keywords:
- C2489
ms.assetid: 67d8cd98-db7e-4f7f-86b4-4af7bc89ec8b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 633a15cfdc05ec2691570b5ecdd91eaf8af9ca78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021384"
---
# <a name="compiler-error-c2489"></a>컴파일러 오류 C2489

'identifier': 'naked' 함수의 함수 범위에서 허용 되지 않습니다 하는 자동 또는 레지스터 변수를 초기화 합니다.

자세한 내용은 [naked](../../cpp/naked-cpp.md)합니다.

다음 샘플에서는 C2489 오류가 생성 됩니다.

```
// C2489.cpp
// processor: x86
__declspec( naked ) int func() {
   int i = 1;   // C2489
   register int j = 1;   // C2489
}
```