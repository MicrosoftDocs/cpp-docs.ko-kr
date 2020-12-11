---
description: '자세한 정보: 컴파일러 오류 C3199'
title: 컴파일러 오류 C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 598d21edbddc91d39edb9623dc59537d3e27bdf3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155477"
---
# <a name="compiler-error-c3199"></a>컴파일러 오류 C3199

부동 소수점 pragma를 잘못 사용 했습니다. 비 precise 모드에서는 예외가 지원 되지 않습니다.

[Float_control](../../preprocessor/float-control.md) pragma가 **/fp: precise** 이외의 [/fp](../../build/reference/fp-specify-floating-point-behavior.md) 설정에서 부동 소수점 예외 모델을 지정 하는 데 사용 되었습니다.

다음 샘플에서는 C3199를 생성 합니다.

```cpp
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```
