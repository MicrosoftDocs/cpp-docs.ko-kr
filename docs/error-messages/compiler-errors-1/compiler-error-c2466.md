---
description: '자세한 정보: 컴파일러 오류 C2466'
title: 컴파일러 오류 C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: 68ff57de2c0287f24ac84466ac8053bf73f88a95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333837"
---
# <a name="compiler-error-c2466"></a>컴파일러 오류 C2466

상수 크기 0의 배열을 할당할 수 없습니다.

크기가 0 인 배열이 할당 되거나 선언 됩니다. 배열 크기에 대 한 상수 식은 0 보다 큰 정수 여야 합니다. 첨자가 0 인 배열 선언은 클래스, 구조체 또는 공용 구조체 멤버와 Microsoft 확장 ([/ze](../../build/reference/za-ze-disable-language-extensions.md)) 에서만 사용할 수 있습니다.

다음 샘플에서는 C2466를 생성 합니다.

```cpp
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```
