---
description: '자세한 정보: 컴파일러 오류 C2491'
title: 컴파일러 오류 C2491
ms.date: 11/04/2016
f1_keywords:
- C2491
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
ms.openlocfilehash: 4fd12e30672d7045aa4a7506b35b845e8cd018c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283707"
---
# <a name="compiler-error-c2491"></a>컴파일러 오류 C2491

'identifier': dllimport 함수를 정의할 수 없습니다.

데이터, 정적 데이터 멤버 및 함수는 `dllimport`로 선언될 수는 있지만 `dllimport`로 정의되지는 않습니다.

이 문제를 해결하려면 함수 정의에서 `__declspec(dllimport)` 지정자를 제거합니다.

다음 샘플에서는 C2491 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C2491.cpp
// compile with: /c
// function definition
void __declspec(dllimport) funcB() {}   // C2491

// function declaration
void __declspec(dllimport) funcB();   // OK
```
