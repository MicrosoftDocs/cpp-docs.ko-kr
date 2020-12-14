---
description: '자세한 정보: 컴파일러 오류 C3264'
title: 컴파일러 오류 C3264
ms.date: 11/04/2016
f1_keywords:
- C3264
helpviewer_keywords:
- C3264
ms.assetid: 94ece687-2364-4f7a-8ebb-7afd3ae9d63d
ms.openlocfilehash: 97edaaf456a0effbd45117eeaea522cfdac0e449
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223427"
---
# <a name="compiler-error-c3264"></a>컴파일러 오류 C3264

'class': 클래스-생성자는 반환 형식을 가질 수 없습니다.

클래스 생성자가 반환 형식을 가질 수 없습니다.

다음 샘플에서는 C3264를 생성합니다.

```cpp
// C3264_2.cpp
// compile with: /clr

ref class X {
   public:
      static int X()   { // C3264
      }

      /* use the code below to resolve the error
      static X() {
      }
      */
};
int main() {
}
```
