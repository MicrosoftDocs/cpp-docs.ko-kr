---
description: '자세한 정보: 컴파일러 오류 C2562'
title: 컴파일러 오류 C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: 9e9da8a7463b450073f4b537ec36512242995760
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338714"
---
# <a name="compiler-error-c2562"></a>컴파일러 오류 C2562

' identifier ': ' void ' 함수에서 값을 반환 합니다.

함수는로 선언 **`void`** 되었지만 값을 반환 합니다.

이 오류는 잘못 된 함수 프로토타입이 원인일 수 있습니다.

이 오류는 함수 선언에서 반환 형식을 지정 하는 경우 수정할 수 있습니다.

다음 샘플에서는 C2562를 생성 합니다.

```cpp
// C2562.cpp
// compile with: /c
void testfunc() {
   int i;
   return i;   // C2562 delete the return to resolve
}
```
