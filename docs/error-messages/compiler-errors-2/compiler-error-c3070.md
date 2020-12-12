---
description: '자세한 정보: 컴파일러 오류 C3070'
title: 컴파일러 오류 C3070
ms.date: 11/04/2016
f1_keywords:
- C3070
helpviewer_keywords:
- C3070
ms.assetid: ac88584d-40a6-4176-90f3-2371c3c935f2
ms.openlocfilehash: 223492901df335102db7285eacaaa946a54e3eaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320294"
---
# <a name="compiler-error-c3070"></a>컴파일러 오류 C3070

'property': 속성에 'set' 메서드가 없습니다.

속성의 set 접근자 메서드가 정의되지 않았습니다. 자세한 내용은 [property](../../extensions/property-cpp-component-extensions.md)을 참조하세요.

다음 샘플에서는 C3070을 생성합니다.

```cpp
// C3070.cpp
// compile with: /clr
ref class R {
public:
   R(int size) {
      m_data = gcnew array<int>(size);
   }

   property int % MyProp[int] {
      int% get(int index) {
         return m_data[index];
      }
   }

   property int % MyProp2[int] {
      int% get(int index) {
         return m_data[index];
      }
      void set(int index, int % value) {}
   }

   property const int % MyProp3[int] {
      const int% get(int index) {
         return m_data[index];
      }
      void set(int index, const int % value) {}
   }

private:
   array<int>^ m_data;
};

int main() {
   R^ r = gcnew R(10);
   r->MyProp[4] = 4;   // C3070

   int value = 4;
   r->MyProp2[4] = value;   // OK
   r->MyProp3[4] = 4;   // OK
}
```
