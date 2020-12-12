---
description: '자세한 정보: 컴파일러 오류 C2823'
title: 컴파일러 오류 C2823
ms.date: 11/04/2016
f1_keywords:
- C2823
helpviewer_keywords:
- C2823
ms.assetid: 982b1b35-1a7c-456e-b711-f80cfe2d571e
ms.openlocfilehash: 57dacaf144f23a1e8486d6a2849fffce0ff8be52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194672"
---
# <a name="compiler-error-c2823"></a>컴파일러 오류 C2823

> typedef 템플릿이 잘못 되었습니다.

템플릿은 정의에서 허용 되지 않습니다 **`typedef`** .

## <a name="example"></a>예제

다음 샘플에서는 C2823를 생성 하 고이를 해결 하는 한 가지 방법을 보여 줍니다.

```cpp
// C2823.cpp
template<class T>
typedef struct x {
   T i;   // C2823 can't use T, specify data type and delete template
   int i;   // OK
} x1;
```
