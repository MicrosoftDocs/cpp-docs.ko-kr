---
description: '자세한 정보: 컴파일러 오류 C3769'
title: 컴파일러 오류 C3769
ms.date: 11/04/2016
f1_keywords:
- C3769
helpviewer_keywords:
- C3769
ms.assetid: 341675e1-7428-4da6-8275-1b2f0a70dacc
ms.openlocfilehash: 5ed980ed75997637a59c6f2a0f864a20297e9a97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291703"
---
# <a name="compiler-error-c3769"></a>컴파일러 오류 C3769

' type ': 중첩 된 클래스는 바로 바깥쪽 클래스와 같은 이름을 사용할 수 없습니다.

중첩 된 클래스는 바로 바깥쪽 클래스와 동일한 이름을 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3769를 생성 합니다.

```cpp
// C3769.cpp
// compile with: /c
class x {
   class x {};   // C3769
   class y {
      class x{};   // OK
   };
};
```
