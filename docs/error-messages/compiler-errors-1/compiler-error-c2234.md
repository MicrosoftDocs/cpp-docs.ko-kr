---
title: 컴파일러 오류 C2234
ms.date: 11/04/2016
f1_keywords:
- C2234
helpviewer_keywords:
- C2234
ms.assetid: cfa42458-c803-4717-a017-9eca1c0cbfb0
ms.openlocfilehash: 16cc09f43f8705452c207e5218f4cc274557e825
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611473"
---
# <a name="compiler-error-c2234"></a>컴파일러 오류 C2234

'name': 참조 배열이 잘못 되었습니다.

없으므로 참조에 대 한 포인터, 참조 배열이 가능 하지 않습니다.

다음 샘플에서는 C2234 오류가 생성 됩니다.

```
// C2234.cpp
int main() {
   int i = 0, j = 0, k = 0, l = 0;
   int &array[4] = {i,j,k,l};   // C2234
   int array2[4] = {i,j,k,l};   // OK
}
```