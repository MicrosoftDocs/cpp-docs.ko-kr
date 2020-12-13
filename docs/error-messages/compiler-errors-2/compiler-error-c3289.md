---
description: '자세한 정보: 컴파일러 오류 C3289'
title: 컴파일러 오류 C3289
ms.date: 11/04/2016
f1_keywords:
- C3289
helpviewer_keywords:
- C3289
ms.assetid: 3c1c623b-7fcf-43ab-a89a-8722532a8d29
ms.openlocfilehash: 12c1f14d1760256f38f225c6215fd41de930d2c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144783"
---
# <a name="compiler-error-c3289"></a>컴파일러 오류 C3289

'property': trivial 속성은 인덱싱할 수 없습니다.

속성이 잘못 선언되었습니다. 인덱싱된 속성에 대해 접근자를 정의해야 합니다. 자세한 내용은 [property](../../extensions/property-cpp-component-extensions.md) 를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3289를 생성합니다.

```cpp
// C3289.cpp
// compile with: /clr
public ref struct C {
   // user-defined simple indexer
   property int indexer1[int];   // C3289

   // user-defined indexer
   property int indexer2[int] {
      int get(int i) { return 0; }
      void set(int i, int j) {}
   }
};

int main() {
   C ^ MyC = gcnew C();
   MyC->indexer2[0] = 1;
}
```
