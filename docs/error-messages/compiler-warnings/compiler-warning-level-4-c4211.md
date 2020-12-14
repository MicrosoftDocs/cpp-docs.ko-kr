---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4211'
title: 컴파일러 경고(수준 4) C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: bbd6469dc98d95342538bf3a9065b4647619d69a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314739"
---
# <a name="compiler-warning-level-4-c4211"></a>컴파일러 경고(수준 4) C4211

비표준 확장이 사용 됨: extern에서 static으로 재정의 되었습니다.

기본 Microsoft 확장 (/Ze)을 사용 하면 식별자를로 재정의할 수 있습니다 **`extern`** **`static`** .

## <a name="example"></a>예제

```c
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

이러한 재정의는 ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))에서 유효 하지 않습니다.
