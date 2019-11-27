---
title: 컴파일러 경고(수준 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 85f37810708eff43574129f42dd8444fe7dc37c2
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541907"
---
# <a name="compiler-warning-level-4-c4214"></a>컴파일러 경고(수준 4) C4214

비표준 확장이 사용 됨: 비트 필드 형식이 int가 아닙니다.

기본 Microsoft 확장 (/Ze)을 사용 하는 경우에는 비트 필드의 경우 모든 정수 형식이 될 수 있습니다.

## <a name="example"></a>예제

```c
// C4214.c
// compile with: /W4
struct bitfields
{
   unsigned short j:4;  // C4214
};

int main()
{
}
```

이러한 비트 필드는 ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))에서 유효 하지 않습니다.