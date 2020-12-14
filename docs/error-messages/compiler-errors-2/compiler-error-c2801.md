---
description: '자세한 정보: 컴파일러 오류 C2801'
title: 컴파일러 오류 C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: ca7e74f99b91b5a6699cdf3361ab64a89b7a7392
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297475"
---
# <a name="compiler-error-c2801"></a>컴파일러 오류 C2801

' operator operator '는 비정적 멤버 여야 합니다.

다음 연산자는 비정적 멤버로만 오버 로드 될 수 있습니다.

- 배정을 `=`

- 클래스 멤버 액세스 `->`

- 첨자 `[]`

- 함수 호출 `()`

가능한 C2801 원인은 다음과 같습니다.

- 오버 로드 된 연산자가 클래스, 구조체 또는 공용 구조체 멤버가 아닙니다.

- 오버 로드 된 연산자가 선언 되었습니다 **`static`** .

- 다음 샘플에서는 C2801를 생성 합니다.

```cpp
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```
