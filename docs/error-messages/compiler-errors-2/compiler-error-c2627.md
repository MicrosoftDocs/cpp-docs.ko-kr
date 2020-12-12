---
description: '자세한 정보: 컴파일러 오류 C2627'
title: 컴파일러 오류 C2627
ms.date: 11/04/2016
f1_keywords:
- C2627
helpviewer_keywords:
- C2627
ms.assetid: 7fc6c5ac-c7c9-4f0b-ad52-f52252526458
ms.openlocfilehash: 4f09e2b76376871dab93e0736c8a0ca6dbb2b5a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174574"
---
# <a name="compiler-error-c2627"></a>컴파일러 오류 C2627

' function ': 익명 공용 구조체에는 멤버 함수를 사용할 수 없습니다.

[익명 공용 구조체](../../cpp/unions.md#anonymous_unions) 에는 멤버 함수를 사용할 수 없습니다.

다음 샘플에서는 C2627를 생성 합니다.

```cpp
// C2627.cpp
int main() {
   union { void f(){} };   // C2627
   union X { void f(){} };
}
```
