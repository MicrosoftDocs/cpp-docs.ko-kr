---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4534'
title: 컴파일러 경고(수준 3) C4534
ms.date: 11/04/2016
f1_keywords:
- c4534
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
ms.openlocfilehash: 6a13b27716488fa04f6342da76fdcd32c5635f2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257890"
---
# <a name="compiler-warning-level-3-c4534"></a>컴파일러 경고(수준 3) C4534

기본 인수로 인해 ' n a t e '는 ' class ' 클래스의 기본 생성자가 되지 않습니다.

관리 되지 않는 클래스에는 기본값이 있는 매개 변수가 있는 생성자가 있을 수 있으며, 컴파일러는이를 기본 생성자로 사용 합니다. 키워드로 표시 된 클래스는 `value` 매개 변수의 기본값을 기본 생성자로 사용 하는 생성자를 사용 하지 않습니다.

자세한 내용은 [클래스 및 구조체](../../extensions/classes-and-structs-cpp-component-extensions.md)를 참조하세요.

다음 샘플에서는 C4534를 생성 합니다.

```cpp
// C4534.cpp
// compile with: /W3 /clr /WX
value class MyClass {
public:
   int ii;
   MyClass(int i = 9) {   // C4534, will not be the default constructor
      i++;
   }
};

int main() {
   MyClass ^ xx = gcnew MyClass;
   xx->ii = 0;
}
```
