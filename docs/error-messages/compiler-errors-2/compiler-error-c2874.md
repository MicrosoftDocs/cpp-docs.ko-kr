---
description: '자세한 정보: 컴파일러 오류 C2874'
title: 컴파일러 오류 C2874
ms.date: 11/04/2016
f1_keywords:
- C2874
helpviewer_keywords:
- C2874
ms.assetid: b54fa9d8-8df5-40d9-9b3b-aa3e9dd6a3be
ms.openlocfilehash: ac8ba9be942be7ab0179640a260d421560a6e406
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320537"
---
# <a name="compiler-error-c2874"></a>컴파일러 오류 C2874

using 선언을 사용 하면 ' symbol '의 여러 선언이 발생 합니다.

선언으로 인해 동일한 항목이 두 번 정의 됩니다.

다음 샘플에서는 C2874를 생성 합니다.

```cpp
// C2874.cpp
namespace Z {
   int i;
}

int main() {
   int i;
   using Z::i;   // C2874, i already declared
}
```
