---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4218'
title: 컴파일러 경고(수준 1) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: 76fc53a5b290a55c73fe036e2fc02b7a1afedd23
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266418"
---
# <a name="compiler-warning-level-1-c4218"></a>컴파일러 경고(수준 1) C4218

비표준 확장이 사용 됨: 저장소 클래스 또는 형식을 하나 이상 지정 해야 합니다.

기본 Microsoft 확장 (/Ze)을 사용 하면 형식 또는 저장소 클래스를 지정 하지 않고 변수를 선언할 수 있습니다. 기본 형식은 **`int`** 입니다.

## <a name="example"></a>예제

```cpp
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

이러한 선언은 ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))에서 유효 하지 않습니다.
