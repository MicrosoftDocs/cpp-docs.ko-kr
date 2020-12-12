---
description: '자세한 정보: 컴파일러 오류 C3414'
title: 컴파일러 오류 C3414
ms.date: 11/04/2016
f1_keywords:
- C3414
helpviewer_keywords:
- C3414
ms.assetid: 715f5432-b509-4f8f-84f5-e1463bac490f
ms.openlocfilehash: c16f57be5665110d8186bdedbb2ada0ac2fdacaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321929"
---
# <a name="compiler-error-c3414"></a>컴파일러 오류 C3414

' member ': 가져온 멤버 함수를 정의할 수 없습니다.

멤버가 참조 된 어셈블리에도 정의 된 코드에서 정의 되었습니다.

다음 샘플에서는 C3414를 생성 합니다.

```cpp
// C3414a2.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

그리고

```cpp
// C3414b2.cpp
// compile with: /clr
#using <C3414a2.dll>

void MyClass::Test() {    // C3414
}

System::Object::Object() {    // C3414
}
```
