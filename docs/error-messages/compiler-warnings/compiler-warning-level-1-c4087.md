---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4087'
title: 컴파일러 경고(수준 1) C4087
ms.date: 11/04/2016
f1_keywords:
- C4087
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
ms.openlocfilehash: 2375ad5c99862f7ee8a0156ca1b3d637b95f0569
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267549"
---
# <a name="compiler-warning-level-1-c4087"></a>컴파일러 경고(수준 1) C4087

'function': 'void' 매개 변수 목록을 사용하여 선언되었습니다.

함수 선언에 정식 매개 변수가 없지만 함수 호출에 실제 매개 변수가 있습니다. 추가 매개 변수는 함수 호출 규칙에 따라 전달됩니다.

이 경고는 C 컴파일러용입니다.

## <a name="example"></a>예제

```c
// C4087.c
// compile with: /W1
int f1( void ) {
}

int main() {
   f1( 10 );   // C4087
}
```
