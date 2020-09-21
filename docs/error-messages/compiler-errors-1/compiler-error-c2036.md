---
title: 컴파일러 오류 C2036
ms.date: 11/04/2016
f1_keywords:
- C2036
helpviewer_keywords:
- C2036
ms.assetid: 895821a9-65d1-44b5-bde1-dae827f3e486
ms.openlocfilehash: 06d292224108434065dfdca2a75d38fd3bb0243c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742699"
---
# <a name="compiler-error-c2036"></a>컴파일러 오류 C2036

' identifier ': 알 수 없는 크기입니다.

에 대 한 작업에는 `identifier` 확인할 수 없는 데이터 개체의 크기가 필요 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2036를 생성 합니다.

```c
// C2036.c
// a C program
struct A* pA;
struct B { int i; } *pB;
int main() {
   pA++;   // C2036, size of A not known
   ((char*)pA)++;   // OK

   pB++;   // OK
}
```

다음 샘플에서는 C2036를 생성 합니다.

```cpp
// C2036_2.cpp
// a C++ program
struct A* pA;
int main() {
   pA++;   // C2036, size of A not known
   ((char*&)pA)++;   // OK, if sizeof(A) == sizeof(char)
}
```
