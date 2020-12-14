---
description: '자세한 정보: 컴파일러 오류 C3452'
title: 컴파일러 오류 C3452
ms.date: 11/04/2016
f1_keywords:
- C3452
helpviewer_keywords:
- C3452
ms.assetid: e5293dcf-cb70-4133-ae2a-0bb496950ba0
ms.openlocfilehash: 7153088ccd132112f47823cd1eb1147480615fc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315988"
---
# <a name="compiler-error-c3452"></a>컴파일러 오류 C3452

목록 인수 멤버가 상수가 아닙니다.

인수가 컴파일 시간에 계산할 수 있는 값인 상수가 필요한 특성에 전달되었습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3452를 생성합니다.

```cpp
// C3452.cpp
// compile with: /c
int i;
[module( name="mod", type=dll, custom={i} ) ];   // C3452
// try the following line instead
// [module( name="mod", type=dll, custom={"a"} ) ];
```
