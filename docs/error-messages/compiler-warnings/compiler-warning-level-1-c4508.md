---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4508'
title: 컴파일러 경고(수준 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: 4394f102c91934a949cdbbc82418d136187cbb7b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294849"
---
# <a name="compiler-warning-level-1-c4508"></a>컴파일러 경고(수준 1) C4508

' function ': 함수는 값을 반환 해야 합니다. ' void ' 반환 형식으로 간주 됩니다.

함수에 지정 된 반환 형식이 없습니다. 이 경우에도 C4430가 실행 되 고 컴파일러가 C4430에서 보고 한 수정 프로그램을 구현 합니다 (기본값은 int).

이 경고를 해결 하려면 함수의 반환 형식을 명시적으로 선언 합니다.

다음 샘플에서는 C4508를 생성 합니다.

```cpp
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```
