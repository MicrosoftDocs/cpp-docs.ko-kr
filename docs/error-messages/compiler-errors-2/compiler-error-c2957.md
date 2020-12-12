---
description: '자세한 정보: 컴파일러 오류 C2957'
title: 컴파일러 오류 C2957
ms.date: 11/04/2016
f1_keywords:
- C2957
helpviewer_keywords:
- C2957
ms.assetid: 9cb4526f-4af8-47e9-b786-56192627ca72
ms.openlocfilehash: 7d5539f43651feb930b3eb0f81677aaed0fa6b4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210584"
---
# <a name="compiler-error-c2957"></a>컴파일러 오류 C2957

'delim': 왼쪽 구분 기호가 잘못되었습니다. '<'가 필요합니다.

제네릭 클래스의 형식이 잘못되었습니다.

다음 샘플에서는 C2957을 생성합니다.

```cpp
// C2957.cpp
// compile with: /clr /LD
generic << class T>   // C2957
// try the following line instead
// generic < class T>
gc class C {};
```
