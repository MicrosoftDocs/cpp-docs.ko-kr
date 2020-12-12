---
description: '자세한 정보: 컴파일러 오류 C2663'
title: 컴파일러 오류 C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: 3e70e2d10b0a133769d92ce637bd9e5f4d44315a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169985"
---
# <a name="compiler-error-c2663"></a>컴파일러 오류 C2663

' function ': 숫자 오버 로드에 ' this ' 포인터에 대 한 올바른 변환이 없습니다.

컴파일러가 **`this`** 멤버 함수의 오버 로드 된 버전으로 변환할 수 없습니다.

이 오류는 개체에 대 한 비멤버 함수를 호출 하 여 발생할 수 있습니다 **`const`** **`const`** .  가능한 해결 방법은 다음과 같습니다.

1. **`const`** 개체 선언에서을 제거 합니다.

1. **`const`** 멤버 함수 오버 로드 중 하나에를 추가 합니다.

다음 샘플에서는 C2663를 생성 합니다.

```cpp
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```
