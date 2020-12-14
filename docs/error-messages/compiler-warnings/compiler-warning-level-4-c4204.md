---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4204'
title: 컴파일러 경고(수준 4) C4204
ms.date: 11/04/2016
f1_keywords:
- C4204
helpviewer_keywords:
- C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
ms.openlocfilehash: edb802e1aa958e28d0a41f3cc64f5ddf058db909
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314791"
---
# <a name="compiler-warning-level-4-c4204"></a>컴파일러 경고(수준 4) C4204

비표준 확장이 사용 됨: 비상수 집합체 이니셜라이저입니다.

Microsoft 확장 (/Ze)을 사용 하면 상수가 아닌 값을 사용 하 여 집계 형식 (배열, 구조체, 공용 구조체 및 클래스)을 초기화할 수 있습니다.

## <a name="example"></a>예제

```c
// C4204.c
// compile with: /W4
int func1()
{
   return 0;
}
struct S1
{
   int i;
};

int main()
{
   struct S1 s1 = { func1() };   // C4204
   return s1.i;
}
```

이러한 초기화는 ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))에서 유효 하지 않습니다.
