---
description: '자세한 정보: 컴파일러 오류 C 2512'
title: 컴파일러 오류 C2512
ms.date: 02/09/2018
f1_keywords:
- C2512
helpviewer_keywords:
- C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
ms.openlocfilehash: 40574ab7fc54ba678729429401ed14fefefe9ebd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212911"
---
# <a name="compiler-error-c2512"></a>컴파일러 오류 C2512

> '*identifier*': 사용할 수 있는 적절 한 기본 생성자가 없습니다.

인수를 요구 하지 않는 생성자 인 *기본 생성자* 는 지정 된 클래스, 구조체 또는 공용 구조체에 사용할 수 없습니다. 컴파일러는 사용자 정의 생성자를 제공 하지 않는 경우에만 기본 생성자를 제공 합니다.

Void가 아닌 매개 변수를 사용 하는 생성자를 제공 하 고 매개 변수 없이 (예: 배열의 요소로) 클래스를 만들 수 있도록 허용 하려면 기본 생성자도 제공 해야 합니다. 기본 생성자는 모든 매개 변수에 기본값을 사용하는 생성자일 수 있습니다.

## <a name="example"></a>예제

오류 C 2512의 일반적인 원인은 인수를 사용 하는 클래스 또는 구조체 생성자를 정의한 다음 인수 없이 클래스 또는 구조체의 인스턴스를 선언 하려고 하는 경우입니다. 예를 들어 `struct B` 다음은 인수를 사용 하지 않는 생성자를 선언 하지만 인수를 사용 하지 않는 생성자는 선언 `char *` 합니다. 에서는 `main` B의 인스턴스가 선언 되지만 인수가 제공 되지 않습니다. 컴파일러는 B에 대 한 기본 생성자를 찾을 수 없기 때문에 C 2512를 생성 합니다.

```cpp
// C2512.cpp
// Compile with: cl /W4 c2512.cpp
// C2512 expected
struct B {
   B (char *) {}
   // Uncomment the following line to fix.
   // B() {}
};

int main() {
   B b;   // C2512 - This requires a default constructor
}
```

등의 구조체 또는 클래스에 대 한 기본 생성자를 정의 `B() {}` 하거나 모든 인수에 기본 값 (예:)이 있는 생성자를 정의 하 여이 문제를 해결할 수 있습니다 `B (char * = nullptr) {}` .
