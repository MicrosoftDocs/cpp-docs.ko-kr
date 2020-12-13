---
description: '자세한 정보: 컴파일러 오류 C3120'
title: 컴파일러 오류 C3120
ms.date: 11/04/2016
f1_keywords:
- C3120
helpviewer_keywords:
- C3120
ms.assetid: 9b6b210f-9948-4517-a4cc-b4aaadebde68
ms.openlocfilehash: 533f0df3da392c36b07af41b9493a7c404972760
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151075"
---
# <a name="compiler-error-c3120"></a>컴파일러 오류 C3120

' method_name ': 인터페이스 메서드는 가변 인수 목록을 사용할 수 없습니다.

인터페이스 메서드는 가변 인수 목록을 사용할 수 없습니다. 예를 들어 다음 인터페이스 정의에서는 C3120를 생성 합니다.

```cpp
// C3120.cpp
__interface A {
int X(int i, ...);    // C3120
};

int main(void) { return(0); }
```
