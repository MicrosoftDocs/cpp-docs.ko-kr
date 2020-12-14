---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4538'
title: 컴파일러 경고(수준 3) C4538
ms.date: 11/04/2016
f1_keywords:
- C4538
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
ms.openlocfilehash: 4f5d6ee8b6144db4fad519f1484d00fe325591a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257851"
---
# <a name="compiler-warning-level-3-c4538"></a>컴파일러 경고(수준 3) C4538

' type ':이 형식에는 const/volatile 한정자를 사용할 수 없습니다.

한정자 키워드가 배열에 잘못 적용 되었습니다. 자세한 내용은 [배열](../../extensions/arrays-cpp-component-extensions.md)을 참조하세요.

다음 샘플에서는 C4538를 생성 합니다.

```cpp
// C4538.cpp
// compile with: /clr /W3 /LD
const array<int> ^f1();   // C4538
array<const int> ^f2();   // OK
```
