---
description: '자세한 정보: 컴파일러 오류 C2380'
title: 컴파일러 오류 C2380
ms.date: 11/04/2016
f1_keywords:
- C2380
helpviewer_keywords:
- C2380
ms.assetid: 717b1e6e-ddfe-4bac-a5f3-7f9a4dcb1572
ms.openlocfilehash: 4455fef072b6d8f686d5f43130db8d02aba69fd1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174691"
---
# <a name="compiler-error-c2380"></a>컴파일러 오류 C2380

' identifier ' 앞의 형식 (반환 형식이 있는 생성자 또는 현재 클래스 이름에 대 한 잘못 된 재정의)

생성자는 값을 반환 하거나 클래스 이름을 다시 정의 합니다.

다음 샘플에서는 C2326을 생성합니다.

```cpp
// C2380.cpp
// compile with: /c
class C {
public:
   int C();   // C2380, specifies an int return
   int C;   // C2380, redefinition of i
   C();   // OK
};
```
