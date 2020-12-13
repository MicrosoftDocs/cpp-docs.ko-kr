---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4366'
title: 컴파일러 경고(수준 4) C4366
ms.date: 11/04/2016
f1_keywords:
- C4366
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
ms.openlocfilehash: 9fa703d64ca48090d3bf6c2f5d9e21668d9acd71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330594"
---
# <a name="compiler-warning-level-4-c4366"></a>컴파일러 경고(수준 4) C4366

단항 ' operator ' 연산자의 결과가 맞춰지지 않을 수 있습니다.

압축으로 인해 구조체 멤버가 정렬 되지 않을 수 있는 경우 컴파일러는 해당 멤버의 주소가 정렬 된 포인터에 할당 될 때 경고를 표시 합니다. 기본적으로 모든 포인터는 정렬 됩니다.

C4366를 해결 하려면 구조체의 맞춤을 변경 하거나 [__unaligned](../../cpp/unaligned.md) 키워드를 사용 하 여 포인터를 선언 합니다.

자세한 내용은 __unaligned 및 [pack](../../preprocessor/pack.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4366를 생성 합니다.

```cpp
// C4366.cpp
// compile with: /W4 /c
// processor: IPF x64
#pragma pack(1)
struct X {
   short s1;
   int s2;
};

int main() {
   X x;
   short * ps1 = &x.s1;   // OK
   int * ps2 = &x.s2;   // C4366
}
```
