---
description: '자세한 정보: 컴파일러 오류 C2118'
title: 컴파일러 오류 C2118
ms.date: 11/04/2016
f1_keywords:
- C2118
helpviewer_keywords:
- C2118
ms.assetid: bf4315d0-f085-4323-b813-96ee61a13bde
ms.openlocfilehash: 89ddf355e233e4fb2d6f36a53369d85bf8ea019a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170102"
---
# <a name="compiler-error-c2118"></a>컴파일러 오류 C2118

음수 첨자

배열 크기를 정의 하는 값이 최대 배열 크기 보다 크거나 0 보다 작습니다.

다음 샘플에서는 C2118를 생성 합니다.

```cpp
// C2118.cpp
int main() {
   int array1[-1];   // C2118
   int array2[3];   // OK
}
```
