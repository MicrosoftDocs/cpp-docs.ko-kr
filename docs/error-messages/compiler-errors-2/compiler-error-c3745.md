---
description: '자세한 정보: 컴파일러 오류 C3745'
title: 컴파일러 오류 C3745
ms.date: 11/04/2016
f1_keywords:
- C3745
helpviewer_keywords:
- C3745
ms.assetid: 1e64aec5-7e53-47e5-bc7d-3905230cfc66
ms.openlocfilehash: f34d3945761b8d0ba233f3963db9392c3dbcd7c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340218"
---
# <a name="compiler-error-c3745"></a>컴파일러 오류 C3745

' function ': 이벤트만 ' e n t ' 일 수 있습니다.

[__Event](../../cpp/event.md) 키워드를 사용 하 여 정의 된 함수만 [__raise](../../cpp/raise.md) 키워드에 전달할 수 있습니다.

다음 샘플에서는 C3745를 생성 합니다.

```cpp
// C3745.cpp
struct E {
   __event void func();
   void func(int) {
   }

   void func2() {
   }

   void bar() {
      __raise func();
      __raise func(1);   // C3745
      __raise func2();   // C3745
   }
};

int main() {
   E e;
   __raise e.func();
   __raise e.func(1);   // C3745
   __raise e.func2();   // C3745
}
```
