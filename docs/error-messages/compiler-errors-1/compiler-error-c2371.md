---
description: '자세한 정보: 컴파일러 오류 C2371'
title: 컴파일러 오류 C2371
ms.date: 11/04/2016
f1_keywords:
- C2371
helpviewer_keywords:
- C2371
ms.assetid: d383993d-05ef-4e35-8129-3b58a6f7b7b7
ms.openlocfilehash: bc7eb66d0ef56d18b7b032dbef17203f600caa0e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239651"
---
# <a name="compiler-error-c2371"></a>컴파일러 오류 C2371

'identifier': 재정의. 기본 형식이 다릅니다.

식별자가 이미 선언되었습니다.

다음 샘플에서는 C2371을 생성합니다.

```cpp
// C2371.cpp
int main() {
   int i;
   float i;   // C2371, redefinition
   float f;   // OK
}
```
