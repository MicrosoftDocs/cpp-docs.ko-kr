---
description: '자세한 정보: 컴파일러 오류 C2206'
title: 컴파일러 오류 C2206
ms.date: 11/04/2016
f1_keywords:
- C2206
helpviewer_keywords:
- C2206
ms.assetid: d7fba68b-aa28-4885-a9a0-27107358f066
ms.openlocfilehash: 53a4c6e25d7864db9a2c69b7e57e0c73e7a80a28
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245709"
---
# <a name="compiler-error-c2206"></a>컴파일러 오류 C2206

'function': 형식 정의는 함수 정의에 사용할 수 없습니다.

는 **`typedef`** 함수 형식을 정의 하는 데 사용 됩니다.

다음 샘플에서는 C2206을 생성합니다.

```cpp
// C2206.cpp
typedef int functyp();
typedef int MyInt;
functyp func1 {};   // C2206
int main() {
   MyInt i = 0;   // OK
}
```
