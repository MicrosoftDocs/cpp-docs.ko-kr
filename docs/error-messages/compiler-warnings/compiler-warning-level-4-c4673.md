---
title: 컴파일러 경고(수준 4) C4673
ms.date: 11/04/2016
f1_keywords:
- C4673
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
ms.openlocfilehash: ceaa5cd647dfb527713613b9ce3b5cd81a780fd7
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741384"
---
# <a name="compiler-warning-level-4-c4673"></a>컴파일러 경고(수준 4) C4673

' identifier '를 throw 하면 다음 형식이 catch 사이트에서 고려 되지 않습니다.

**Catch** 블록에서 throw 개체를 처리할 수 없습니다. 처리할 수 없는 각 형식은이 경고를 포함 하는 줄 바로 다음에 오는 오류 출력에 나열 됩니다. 처리 되지 않은 각 형식에는 고유한 경고가 있습니다. 자세한 내용은 각 특정 형식에 대 한 경고를 참조 하세요.

다음 샘플에서는 C4673를 생성 합니다.

```
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