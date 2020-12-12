---
description: '자세한 정보: 컴파일러 오류 C2274'
title: 컴파일러 오류 C2274
ms.date: 11/04/2016
f1_keywords:
- C2274
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
ms.openlocfilehash: 31b9d63b9cf87114ce2d1d79f1f38fff97d4ebbb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268355"
---
# <a name="compiler-error-c2274"></a>컴파일러 오류 C2274

' type ': '. ' 연산자의 오른쪽에 사용할 수가 없습니다.

형식이 멤버 액세스 (.) 연산자의 오른쪽 피연산자로 표시 됩니다.

이 오류는 사용자 정의 형식 변환에 액세스 하려고 할 때 발생할 수 있습니다. 마침표와 사이에 키워드를 사용 합니다 **`operator`** `type` .

다음 샘플에서는 C2286을 생성합니다.

```cpp
// C2274.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};

int main() {
   MyClass ClassName;
   int i = ClassName.int();   // C2274
   int j = ClassName.operator int();   // OK
}
```
