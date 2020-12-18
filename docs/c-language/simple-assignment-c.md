---
description: '자세한 정보: 단순 할당 (C)'
title: 단순 할당 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
ms.openlocfilehash: bf8637268c810ed6a75095774ca6ff7b7d3d9e67
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229901"
---
# <a name="simple-assignment-c"></a>단순 할당 (C)

단순 할당 연산자는 오른쪽 피연산자를 왼쪽 피연산자에 할당합니다. 오른쪽 피연산자의 값은 할당 식의 형식으로 변환되며 왼쪽 피연산자로 지정된 개체에 저장된 값을 대체합니다. 할당에 대한 변환 규칙이 적용됩니다([할당 변환](../c-language/assignment-conversions.md) 참조).

```
double x;
int y;

x = y;
```

이 예제에서 `y` 값은 **`double`** 형식으로 변환되어 `x`에 할당됩니다.

## <a name="see-also"></a>참조

[C 할당 연산자](../c-language/c-assignment-operators.md)
