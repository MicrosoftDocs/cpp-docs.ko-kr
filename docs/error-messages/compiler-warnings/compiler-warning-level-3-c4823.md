---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4823'
title: 컴파일러 경고(수준 3) C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: b5f4efcf25e59025ad086832c2446d856918542a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332105"
---
# <a name="compiler-warning-level-3-c4823"></a>컴파일러 경고(수준 3) C4823

' function ': 고정 포인터를 사용 하지만 해제 의미 체계가 활성화 되어 있지 않습니다. /EHa 사용 고려

블록 범위에 선언 된 고정 포인터가 가리키는 관리 되는 힙에서 개체를 고정 해제 하기 위해 컴파일러는 로컬 클래스의 소멸자 동작을 시뮬레이션 합니다. 고정 포인터에는 포인터를 nullifies 하는 소멸자가 있습니다. 예외를 throw 한 후 소멸자를 호출할 수 있도록 하려면 [/ehsc](../../build/reference/eh-exception-handling-model.md)를 사용 하 여 수행할 수 있는 개체 해제를 사용 하도록 설정 해야 합니다.

수동으로 개체의 고정을 해제 하 고 경고를 무시할 수도 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4823를 생성 합니다.

```cpp
// C4823.cpp
// compile with: /clr /W3 /EHa-
using namespace System;

ref struct G {
   int m;
};

void f(G ^ pG) {
   try {
      pin_ptr<int> p = &pG->m;
      // manually unpin, ignore warning
      // p = nullptr;
      throw gcnew Exception;
   }
   catch(Exception ^) {}
}   // C4823 warning

int main() {
   f( gcnew G );
}
```
