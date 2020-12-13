---
description: '자세한 정보: 컴파일러 오류 C2033'
title: 컴파일러 오류 C2033
ms.date: 11/04/2016
f1_keywords:
- C2033
helpviewer_keywords:
- C2033
ms.assetid: fd5a1637-9db2-4c98-a7cc-b63b39737cd9
ms.openlocfilehash: c7beabafb544f1ad76f6a8eabe24bd20a7e63f62
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175432"
---
# <a name="compiler-error-c2033"></a>컴파일러 오류 C2033

'identifier': 비트 필드에 간접 참조를 사용할 수 없습니다.

비트 필드가 허용되지 않는 포인터로 선언되었습니다.

다음 샘플에서는 C2033을 생성합니다.

```cpp
// C2033.cpp
struct S {
   int *b : 1;  // C2033
};
```

해결 방법:

```cpp
// C2033b.cpp
// compile with: /c
struct S {
   int b : 1;
};
```
