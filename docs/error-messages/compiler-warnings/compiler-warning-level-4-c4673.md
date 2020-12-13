---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4673'
title: 컴파일러 경고(수준 4) C4673
ms.date: 11/04/2016
f1_keywords:
- C4673
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
ms.openlocfilehash: 557a8a0049a5870b0ae824f96a96c12ee01c0842
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134006"
---
# <a name="compiler-warning-level-4-c4673"></a>컴파일러 경고(수준 4) C4673

' identifier '를 throw 하면 다음 형식이 catch 사이트에서 고려 되지 않습니다.

Throw 개체는 블록에서 처리할 수 없습니다 **`catch`** . 처리할 수 없는 각 형식은이 경고를 포함 하는 줄 바로 다음에 오는 오류 출력에 나열 됩니다. 처리 되지 않은 각 형식에는 고유한 경고가 있습니다. 자세한 내용은 각 특정 형식에 대 한 경고를 참조 하세요.

다음 샘플에서는 C4673를 생성 합니다.

```cpp
// C4673.cpp
// compile with: /EHsc /W4
class Base {
private:
   char * m_chr;
public:
   Base() {
      m_chr = 0;
   }

   ~Base() {
      if(m_chr)
         delete m_chr;
   }
};

class Derv : private Base {
public:
   Derv() {}
   ~Derv() {}
};

int main() {
   try {
      Derv D1;
      // delete previous line, uncomment the next line to resolve
      // Base D1;
      throw D1;   // C4673
   }

   catch(...) {}
}
```
