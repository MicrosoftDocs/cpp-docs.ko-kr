---
description: '자세한 정보: 컴파일러 오류 C2378'
title: 컴파일러 오류 C2378
ms.date: 11/04/2016
f1_keywords:
- C2378
helpviewer_keywords:
- C2378
ms.assetid: 507a91c6-ca72-48df-b3a4-2cf931c86806
ms.openlocfilehash: 2a608cf2aa031da26356ec1b2643fc033ff9ddf5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174730"
---
# <a name="compiler-error-c2378"></a>컴파일러 오류 C2378

'identifier': 재정의. 형식 정의를 사용하여 기호를 오버로드할 수 없습니다.

식별자가로 다시 정의 되었습니다 **`typedef`** .

다음 샘플에서는 C2378을 생성합니다.

```cpp
// C2378.cpp
// compile with: /c
int i;
typedef int i;   // C2378
typedef int b;   // OK
```
