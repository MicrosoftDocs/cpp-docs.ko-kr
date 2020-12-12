---
description: '자세히 알아보기: novtable'
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: 2c818d07603e294f760b768861ce7e7a3e02894b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146200"
---
# <a name="novtable"></a>novtable

**Microsoft 전용**

**`__declspec`** 확장 특성입니다.

이 형식은 **`__declspec`** 모든 클래스 선언에 적용할 수 있지만 순수 인터페이스 클래스, 즉 자체적으로 인스턴스화되지 않을 클래스에만 적용 해야 합니다. 는 **`__declspec`** 컴파일러가 클래스의 생성자 및 소멸자에서 vfptr을 초기화 하는 코드를 생성 하지 않도록 합니다. 대부분의 경우 이렇게 하면 클래스와 연결된 vtable에 대한 참조만 제거되므로 링커가 이를 제거합니다. 이 형식을 사용 **`__declspec`** 하면 코드 크기가 상당히 줄어들 수 있습니다.

로 표시 된 클래스를 인스턴스화하고 **`novtable`** 클래스 멤버에 액세스 하려는 경우에는 AV (액세스 위반)를 받게 됩니다.

## <a name="example"></a>예제

```cpp
// novtable.cpp
#include <stdio.h>

struct __declspec(novtable) X {
   virtual void mf();
};

struct Y : public X {
   void mf() {
      printf_s("In Y\n");
   }
};

int main() {
   // X *pX = new X();
   // pX->mf();   // Causes a runtime access violation.

   Y *pY = new Y();
   pY->mf();
}
```

```Output
In Y
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`__declspec`](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)
