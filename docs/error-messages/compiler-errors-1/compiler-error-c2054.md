---
description: '자세한 정보: 컴파일러 오류 C2054'
title: 컴파일러 오류 C2054
ms.date: 11/04/2016
f1_keywords:
- C2054
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
ms.openlocfilehash: b86c805a5687679cfa4bb5ed667c3bcf3adbad94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341362"
---
# <a name="compiler-error-c2054"></a>컴파일러 오류 C2054

' identifier '를 따르려면 ' ('가 필요 합니다.

함수 식별자는 후행 괄호가 필요한 컨텍스트에서 사용 됩니다.

이 오류는 복잡 한 초기화에서 등호 (=)를 생략 하 여 발생할 수 있습니다.

다음 샘플에서는 C2054를 생성 합니다.

```c
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

해결 방법:

```c
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```
