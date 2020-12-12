---
description: '자세한 정보: 컴파일러 오류 C2548'
title: 컴파일러 오류 C2548
ms.date: 11/04/2016
f1_keywords:
- C2548
helpviewer_keywords:
- C2548
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
ms.openlocfilehash: cf7686191199ec1d0b5c515138f15f2fbf85efa8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204110"
---
# <a name="compiler-error-c2548"></a>컴파일러 오류 C2548

' class:: member ': 매개 변수 매개 변수에 대 한 기본 매개 변수가 없습니다.

기본 매개 변수 목록에 매개 변수가 없습니다. 매개 변수 목록에 기본 매개 변수를 제공 하는 경우 모든 후속 매개 변수에 대 한 기본 매개 변수를 정의 해야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2548를 생성 합니다.

```cpp
// C2548.cpp
// compile with: /c
void func( int = 1, int, int = 3);  // C2548

// OK
void func2( int, int, int = 3);
void func3( int, int = 2, int = 3);
```
