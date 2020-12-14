---
description: '자세한 정보: 컴파일러 오류 C3736'
title: 컴파일러 오류 C3736
ms.date: 11/04/2016
f1_keywords:
- C3736
helpviewer_keywords:
- C3736
ms.assetid: 579b773c-41e7-40ea-8382-2e3ce2667f4c
ms.openlocfilehash: 6ec22012efb9de3ec7f0b8911ed45f4f6a724135
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244994"
---
# <a name="compiler-error-c3736"></a>컴파일러 오류 C3736

' event ': 메서드 이거나, 관리 되는 이벤트의 경우 선택적으로 데이터 멤버 여야 합니다.

네이티브 및 COM 이벤트는 메서드 여야 합니다. .NET 이벤트는 데이터 멤버일 수도 있습니다.

다음 샘플에서는 C3736를 생성 합니다.

```cpp
// C3736.cpp
struct A {
   __event int e();
};

struct B {
   int f;   // C3736
   // The following line resolves the error.
   // int f();
   B(A* a) {
      __hook(&A::e, a, &B::f);
   }
};

int main() {
}
```
