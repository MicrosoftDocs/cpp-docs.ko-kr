---
title: 컴파일러 경고 (수준 1) C4047
ms.date: 11/04/2016
f1_keywords:
- C4047
helpviewer_keywords:
- C4047
ms.assetid: b75ad6fb-5c93-4434-a85f-c4083051a5de
ms.openlocfilehash: 0bfbcb0e88380dfcc21eb724fc3682ac66b655e6
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624947"
---
# <a name="compiler-warning-level-1-c4047"></a>컴파일러 경고 (수준 1) C4047

'operator' : 'identifier1'의 간접 참조 수준이 'identifier2'와 다릅니다.

포인터는 변수 (한 수준의 간접 참조)를 가리키고 변수 (두 수준의 간접 참조)를 가리키는 다른 포인터를 가리킬 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4047를 생성 합니다.

```c
// C4047.c
// compile with: /W1

int main() {
   char **p = 0;   // two levels of indirection
   char *q = 0;   // one level of indirection

   char *p2 = 0;   // one level of indirection
   char *q2 = 0;   // one level of indirection

   p = q;   // C4047
   p2 = q2;
}
```

## <a name="example"></a>예제

다음 샘플에서는 C4047를 생성 합니다.

```c
// C4047b.c
// compile with: /W1
#include <stdio.h>

int main() {
   int i;
   FILE *myFile = NULL;
   errno_t  err = 0;
   char file_name[256];
   char *cs = 0;

   err = fopen_s(&myFile, "C4047.txt", "r");
   if ((err != 0) || (myFile)) {
      printf_s("fopen_s failed!\n");
      exit(-1);
    }
   i = fgets(file_name, 256, myFile);   // C4047
   cs = fgets(file_name, 256, myFile);   // OK
}
```