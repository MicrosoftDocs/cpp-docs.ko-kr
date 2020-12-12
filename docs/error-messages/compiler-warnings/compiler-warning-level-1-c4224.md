---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4224'
title: 컴파일러 경고(수준 1) C4224
ms.date: 11/04/2016
f1_keywords:
- C4224
helpviewer_keywords:
- C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
ms.openlocfilehash: f9632ec80ee845da6933be22a6e446ac5251257f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266405"
---
# <a name="compiler-warning-level-1-c4224"></a>컴파일러 경고(수준 1) C4224

비표준 확장이 사용 됨: ' identifier ' 정식 매개 변수가 이전에 형식으로 정의 되었습니다.

식별자는 이전에로 사용 되었습니다 **`typedef`** . 이렇게 하면 ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))에서 경고가 발생 합니다.

## <a name="example"></a>예제

```cpp
// C4224.cpp
// compile with: /Za /W1 /LD
typedef int I;
void func ( int I );  // C4224
```
