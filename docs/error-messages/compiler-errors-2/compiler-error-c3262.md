---
description: '자세한 정보: 컴파일러 오류 C3262'
title: 컴파일러 오류 C3262
ms.date: 11/04/2016
f1_keywords:
- C3262
helpviewer_keywords:
- C3262
ms.assetid: 3e74b9aa-de3c-4492-9331-ee73012b958b
ms.openlocfilehash: 9d1b4954f4f015c5dad584a5e6a124bc7d4bd155
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223453"
---
# <a name="compiler-error-c3262"></a>컴파일러 오류 C3262

잘못된 배열 인덱싱: '#'개 차원을 '#'차원 'array type'에 대해 지정했습니다.

배열 아래 첨자가 잘못되었습니다. 인덱스 수가 배열 차원 수와 일치하지 않을 수 있습니다.

다음 샘플에서는 C3262를 생성합니다.

```cpp
// C3262.cpp
// compile with: /clr
#using <mscorlib.dll>
using namespace System;

#define ARRAY_SIZE 2

ref class MyClass {
public:
   int m_i;
};

// returns a multidimensional managed array of a reference type
array<MyClass^, 2>^ Test0() {
   int i, j;
   array< MyClass^, 2 >^ local = new array< MyClass^, 2 >
      (ARRAY_SIZE, ARRAY_SIZE);

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      for (j = 0 ; j < ARRAY_SIZE ; j++) {
         local[i][j] = new MyClass;   // C3262
         // try the following line instead
         // local[i,j] = new MyClass;
         local[i,j] -> m_i = i;
      }

      return local;
}

int main() {
   int i, j;

   array< MyClass^, 2 >^ MyClass0;
   MyClass0 = Test0();
}
```
