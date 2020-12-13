---
description: '자세한 정보: 컴파일러 오류 C2516'
title: 컴파일러 오류 C2516
ms.date: 11/04/2016
f1_keywords:
- C2516
helpviewer_keywords:
- C2516
ms.assetid: cd3accc1-0179-4a13-9587-616908c4ad1d
ms.openlocfilehash: 1561a6917d26a9cc4c71a8970e7a75512c1a1b61
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339294"
---
# <a name="compiler-error-c2516"></a>컴파일러 오류 C2516

' name ': 올바른 기본 클래스가 아닙니다.

클래스는 문에 의해 정의 된 형식 이름에서 파생 됩니다 **`typedef`** .

다음 샘플에서는 C2516를 생성 합니다.

```cpp
// C2516.cpp
typedef unsigned long ulong;
class C : public ulong {}; // C2516
```
