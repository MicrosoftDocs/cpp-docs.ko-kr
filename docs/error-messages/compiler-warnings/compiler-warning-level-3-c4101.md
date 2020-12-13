---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4101'
title: 컴파일러 경고 (수준 3) C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: c5e358bea4e9a584242376ed86d1bb5af2deb734
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150633"
---
# <a name="compiler-warning-level-3-c4101"></a>컴파일러 경고 (수준 3) C4101

' identifier ': 참조 되지 않은 지역 변수입니다.

지역 변수는 사용 되지 않습니다. 이 경고는 다음과 같은 명백한 상황에서 발생 합니다.

```cpp
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

그러나 **`static`** 클래스의 인스턴스를 통해 멤버 함수를 호출 하는 경우에도이 경고가 발생 합니다.

```cpp
// C4101b.cpp
// compile with:  /W3
struct S {
   static int func()
   {
      return 1;
   }
};

int main() {
   S si;   // C4101, si is never used
   int y = si.func();
   return y;
}
```

이 경우 컴파일러는에 대 한 정보를 사용 하 여 `si` 함수에 액세스 **`static`** 하지만 클래스의 인스턴스는 함수를 호출 하는 데 필요 하지 않으므로 경고가 발생 합니다 **`static`** . 이 경고를 해결 하려면 다음을 수행 합니다.

- 컴파일러가에 대 한 호출에서의 인스턴스를 사용 하는 생성자를 추가 `si` `func` 합니다.

- **`static`** 의 정의에서 키워드를 제거 `func` 합니다.

- 함수를 **`static`** 명시적으로 호출 `int y = S::func();` 합니다.
