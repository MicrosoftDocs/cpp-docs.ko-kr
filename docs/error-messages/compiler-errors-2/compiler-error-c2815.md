---
description: '자세한 정보: 컴파일러 오류 C2815'
title: 컴파일러 오류 C2815
ms.date: 11/04/2016
f1_keywords:
- C2815
helpviewer_keywords:
- C2815
ms.assetid: d0256fd6-0721-4c99-b03c-52d96e77a613
ms.openlocfilehash: fd0ee162c10acd89e4746ea906d64ea8ef069271
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194841"
---
# <a name="compiler-error-c2815"></a>컴파일러 오류 C2815

' operator delete ': 첫 번째 정식 매개 변수는 ' void * ' 여야 하는데 ' param '이 (가) 사용 되었습니다.

사용자 정의 [operator delete](../../standard-library/new-operators.md#op_delete) 함수는 유형의 첫 번째 정식 매개 변수를 사용 해야 합니다 `void *` .

다음 샘플에서는 C2815를 생성 합니다.

```cpp
// C2815.cpp
// compile with: /c
class CMyClass {
public:
   void mf1(int *a);
   void operator delete(CMyClass *);   // C2815
   void operator delete(void *);
};
```
