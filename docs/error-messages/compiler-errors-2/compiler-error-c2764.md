---
description: '자세한 정보: 컴파일러 오류 C2764'
title: 컴파일러 오류 C2764
ms.date: 11/04/2016
f1_keywords:
- C2764
helpviewer_keywords:
- C2764
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
ms.openlocfilehash: c700286a840c518597947f21f0455bc711f68275
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239534"
---
# <a name="compiler-error-c2764"></a>컴파일러 오류 C2764

' param ': 템플릿 매개 변수를 사용 하지 않거나 부분 특수화 ' 특수화 '에서 추론할 수 없습니다.

템플릿 매개 변수는 부분 특수화에서 사용 되지 않습니다. 이렇게 하면 템플릿 매개 변수를 추론할 수 없으므로 부분 특수화를 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2764를 생성 합니다.

```cpp
// C2764.cpp
#include <stdio.h>
template <class T1, class T2>
struct S  {
   int m_i;
};

template <class T1, class T2>
struct S<int, T2*> {   // C2764
// try the following line instead
// struct S<T1(*)(T2), T2*> {
   char m_c;
};

int main() {
   S<int, char> s1;
   S<void (*)(short), short *> s2;
   s2.m_c = 10;
   s1.m_i = s2.m_c;
   printf_s("%d\n", s1.m_i);
}
```
