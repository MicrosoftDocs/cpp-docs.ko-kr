---
description: '자세한 정보: 컴파일러 오류 C2570'
title: 컴파일러 오류 C2570
ms.date: 11/04/2016
f1_keywords:
- C2570
helpviewer_keywords:
- C2570
ms.assetid: d65d0b32-2fac-464a-bcdf-0ebcedf3bf32
ms.openlocfilehash: faebc117991262c8fff94ef75f18d6e59c884315
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209024"
---
# <a name="compiler-error-c2570"></a>컴파일러 오류 C2570

' identifier ': 공용 구조체에 기본 클래스를 사용할 수 없습니다.

Union은 클래스, 구조체 또는 공용 구조체에서 파생 됩니다. 이것은 허용되지 않습니다. 대신 파생 형식을 클래스 또는 구조체로 선언 합니다.

다음 샘플에서는 C2570를 생성 합니다.

```cpp
// C2570.cpp
// compile with: /c
class base {};
union hasPubBase : public base {};   // C2570
union hasNoBase {};   // OK
```
