---
description: '자세한 정보: 컴파일러 오류 C2109'
title: 컴파일러 오류 C2109
ms.date: 11/04/2016
f1_keywords:
- C2109
helpviewer_keywords:
- C2109
ms.assetid: 2d1ac79d-a985-4904-a38b-b270578d664d
ms.openlocfilehash: b47a0034aade2c3afda3e6785fa2dcd3215b3356
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341284"
---
# <a name="compiler-error-c2109"></a>컴파일러 오류 C2109

첨자는 배열 또는 포인터 형식이 필요 합니다.

첨자가 배열이 아닌 변수에 사용 되었습니다.

다음 샘플에서는 C2109를 생성 합니다.

```cpp
// C2109.cpp
int main() {
   int a, b[10] = {0};
   a[0] = 1;   // C2109
   b[0] = 1;   // OK
}
```
