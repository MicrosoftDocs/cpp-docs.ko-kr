---
description: '자세한 정보: 컴파일러 오류 C2273'
title: 컴파일러 오류 C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: 656b5477682ace779cd872b2233d911cfb67c0e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336261"
---
# <a name="compiler-error-c2273"></a>컴파일러 오류 C2273

' type ': '-> ' 연산자의 오른쪽에 사용할 수가 잘못 되었습니다.

연산자의 오른쪽 피연산자로 형식이 표시 됩니다 `->` .

이 오류는 사용자 정의 형식 변환에 액세스 하려고 할 때 발생할 수 있습니다. **`operator`**->와 사이에 키워드를 사용 `type` 합니다.

다음 샘플에서는 C2273를 생성 합니다.

```cpp
// C2273.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};
int main() {
   MyClass * ClassPtr = new MyClass;
   int i = ClassPtr->int();   // C2273
   int j = ClassPtr-> operator int();   // OK
}
```
