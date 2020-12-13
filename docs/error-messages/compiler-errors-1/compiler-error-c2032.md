---
description: '자세한 정보: 컴파일러 오류 C2032'
title: 컴파일러 오류 C2032
ms.date: 11/04/2016
f1_keywords:
- C2032
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
ms.openlocfilehash: cb39a539dc1e360f70cc2b217d50f3a1eabcf0f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175458"
---
# <a name="compiler-error-c2032"></a>컴파일러 오류 C2032

' identifier ': 함수는 구조체/공용 구조체 ' structorunion '의 멤버일 수 없습니다.

구조체 또는 공용 구조체에는 c + +에서 허용 되지만 C에서는 허용 되지 않는 멤버 함수가 있습니다. 오류를 해결 하려면 c + + 프로그램으로 컴파일하거나 멤버 함수를 제거 합니다.

다음 샘플에서는 C2032를 생성 합니다.

```c
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

해결 방법:

```c
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```
