---
description: '자세한 정보: 컴파일러 오류 C2021'
title: 컴파일러 오류 C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 823d9c3d42f1df7bc6f6f398dafd804daef76110
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175640"
---
# <a name="compiler-error-c2021"></a>컴파일러 오류 C2021

'character'가 아니라 지수 값이 필요합니다.

부동 소수점 상수의 지 수로 사용 되는 문자가 유효한 숫자가 아닙니다. 범위에 있는 지 수를 사용 해야 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2021를 생성 합니다.

```cpp
// C2021.cpp
float test1=1.175494351E;   // C2021
```

해결 방법:

```cpp
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```
