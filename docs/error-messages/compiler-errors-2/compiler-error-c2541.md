---
description: '자세한 정보: 컴파일러 오류 C2541'
title: 컴파일러 오류 C2541
ms.date: 11/04/2016
f1_keywords:
- C2541
helpviewer_keywords:
- C2541
ms.assetid: ed95180f-00df-4e62-a8e9-1b6dab8281bf
ms.openlocfilehash: 79d4cab33a7c92455b5a4eacdf75f26f80b16a33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302012"
---
# <a name="compiler-error-c2541"></a>컴파일러 오류 C2541

' delete ': delete: 포인터가 아닌 개체를 삭제할 수 없습니다.

[Delete](../../cpp/delete-operator-cpp.md) 연산자가 포인터가 아닌 개체에서 사용 되었습니다.

다음 샘플에서는 C2541를 생성 합니다.

```cpp
// C2541.cpp
int main() {
   int i;
   delete i;   // C2541 i not a pointer

   // OK
   int *ip = new int;
   delete ip;
}
```
