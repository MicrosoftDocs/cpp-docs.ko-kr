---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4213'
title: 컴파일러 경고(수준 4) C4213
ms.date: 11/04/2016
f1_keywords:
- C4213
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
ms.openlocfilehash: 400cd650542bfd7a71640947467e8340f63bb3df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297345"
---
# <a name="compiler-warning-level-4-c4213"></a>컴파일러 경고(수준 4) C4213

비표준 확장이 사용 됨: l-value를 캐스트 합니다.

기본 Microsoft 확장 (/Ze)을 사용 하면 대입문의 왼쪽에서 캐스트를 사용할 수 있습니다.

## <a name="example"></a>예제

```c
// C4213.c
// compile with: /W4
void *a;
void f()
{
   int   i[3];
   a = &i;
   *(( int * )a )++ = 3;  // C4213
}

int main()
{
}
```

이러한 캐스트는 ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))에서 유효 하지 않습니다.
