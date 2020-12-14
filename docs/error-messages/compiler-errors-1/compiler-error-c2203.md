---
description: '자세한 정보: 컴파일러 오류 C2203'
title: 컴파일러 오류 C2203
ms.date: 11/04/2016
f1_keywords:
- C2203
helpviewer_keywords:
- C2203
ms.assetid: 5497df43-86f6-43d5-b6cb-723c4c589b10
ms.openlocfilehash: 98da34221da5bc054de795579d33be00fb3657cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245787"
---
# <a name="compiler-error-c2203"></a>컴파일러 오류 C2203

delete 연산자는 배열의 범위를 지정할 수 없습니다.

**/Za** (ANSI) 옵션을 사용 하는 경우 **`delete`** 연산자는 전체 배열을 삭제할 수 있지만 배열의 부분이 나 특정 멤버는 삭제할 수 없습니다.

다음 샘플에서는 C2203를 생성 합니다.

```cpp
// C2203.cpp
// compile with: /Za
int main() {
   int *ar = new int[10];
   delete [4] ar;   // C2203
   // try the following line instead
   // delete [] ar;
}
```
