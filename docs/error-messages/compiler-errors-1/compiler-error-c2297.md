---
description: '자세한 정보: 컴파일러 오류 C2297'
title: 컴파일러 오류 C2297
ms.date: 11/04/2016
f1_keywords:
- C2297
helpviewer_keywords:
- C2297
ms.assetid: 65849fe5-17e1-4b7e-b50c-f508b05ddaa4
ms.openlocfilehash: d9843592a366054d72b3cc179aec6da85843f105
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235205"
---
# <a name="compiler-error-c2297"></a>컴파일러 오류 C2297

' operator ': 잘못 된 오른쪽 피연산자입니다.

에 사용 된 오른쪽 피연산자 `operator` 가 잘못 되었습니다.

예를 들어 컴파일러는 함수 호출을 의도 한 선언을 볼 수 있습니다.

다음 샘플에서는 C2297를 생성 합니다.

```cpp
// C2297.cpp
struct MyStruct {
   struct Help {
      Help(float f) : m_f(f) {}
      float m_f;
   };

   MyStruct(const Help &h) : m_f(h.m_f) {}

   MyStruct(float f) : m_f(f) {}

   MyStruct operator*(const MyStruct &f1) const {
      return MyStruct(m_f * f1.m_f);
   }

private:
   float m_f;
};

int main() {
   float f1 = 1.0f;

   MyStruct m_MyStruct1 ( MyStruct::Help( f1 ) );
   // try the following line instead
   // MyStruct m_MyStruct1 = MyStruct::Help( f1 );

   MyStruct m_MyStruct2 ( MyStruct::Help( f1 ) );
   // try the following line instead
   // MyStruct m_MyStruct2 = MyStruct::Help( f1 );

   MyStruct m_MyStruct3 = m_MyStruct1 * m_MyStruct2;   // C2297
}
```
