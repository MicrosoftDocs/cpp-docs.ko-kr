---
description: '자세한 정보: 컴파일러 오류 C2229'
title: 컴파일러 오류 C2229
ms.date: 11/04/2016
f1_keywords:
- C2229
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
ms.openlocfilehash: d95d1248ec7e555af0c4ecfffa25dc69af288458
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194984"
---
# <a name="compiler-error-c2229"></a>컴파일러 오류 C2229

' identifier ' 형식에 잘못 된 크기가 0 인 배열이 있습니다.

구조체 또는 비트 필드의 멤버에 마지막 멤버가 아닌 크기가 0 인 배열이 포함 되어 있습니다.

구조체의 마지막 멤버로 크기가 0 인 배열을 사용할 수 있으므로 구조체를 할당할 때 크기를 지정 해야 합니다.

크기가 0 인 배열이 구조체의 마지막 멤버가 아닌 경우 컴파일러는 나머지 필드의 오프셋을 계산할 수 없습니다.

다음 샘플에서는 C2229를 생성 합니다.

```cpp
// C2229.cpp
struct S {
   int a[0];  // C2229  zero-sized array
   int b[1];
};

struct S2 {
   int a;
   int b[0];
};

int main() {
   // allocate 7 elements for b field
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];
   s2->b[6] = 100;
}
```
