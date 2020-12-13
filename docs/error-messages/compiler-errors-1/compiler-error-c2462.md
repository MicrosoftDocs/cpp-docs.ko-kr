---
description: '자세한 정보: 컴파일러 오류 C2462'
title: 컴파일러 오류 C2462
ms.date: 11/04/2016
f1_keywords:
- C2462
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
ms.openlocfilehash: f85d8f2e38c38043765b29b6e766c0cbd4fef1fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341817"
---
# <a name="compiler-error-c2462"></a>컴파일러 오류 C2462

' identifier ': ' 새 식 '에 형식을 정의할 수 없습니다.

연산자의 피연산자 필드에 형식을 정의할 수 없습니다 **`new`** . 형식 정의를 별도의 문에 배치 합니다.

다음 샘플에서는 C2462를 생성 합니다.

```cpp
// C2462.cpp
int main() {
   new struct S { int i; };   // C2462
}
```
