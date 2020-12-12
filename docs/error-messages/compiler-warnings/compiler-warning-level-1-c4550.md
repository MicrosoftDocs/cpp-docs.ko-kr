---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4550'
title: 컴파일러 경고(수준 1) C4550
ms.date: 11/04/2016
f1_keywords:
- C4550
helpviewer_keywords:
- C4550
ms.assetid: f902b4ed-5f17-48ea-b693-92f4fb8c8054
ms.openlocfilehash: 8edb7744f522312933bcf9d273982e591918dac2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265976"
---
# <a name="compiler-warning-level-1-c4550"></a>컴파일러 경고(수준 1) C4550

식이 인수 목록이 없는 함수로 계산 됩니다.

함수에 대 한 역참조 된 포인터에 인수 목록이 없습니다.

## <a name="example"></a>예제

```cpp
// C4550.cpp
// compile with: /W1
bool f()
{
   return true;
}

typedef bool (*pf_t)();

int main()
{
   pf_t pf = f;
   if (*pf) {}  // C4550
   return 0;
}
```
