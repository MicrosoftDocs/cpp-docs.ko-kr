---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4346'
title: 컴파일러 경고(수준 1) C4346
ms.date: 11/04/2016
f1_keywords:
- C4346
helpviewer_keywords:
- C4346
ms.assetid: 68ee562d-cca9-4a2a-9a1b-14ad1a1e7396
ms.openlocfilehash: 587aaf6954bb649ab12478721fcf428ef3611329
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340011"
---
# <a name="compiler-warning-level-1-c4346"></a>컴파일러 경고(수준 1) C4346

' name ': 종속 이름이 형식이 아닙니다.

형식으로 처리 해야 하는 종속 이름이 있는 경우 [typename](../../cpp/typename.md) 키워드를 입력 해야 합니다. 모든 버전의 Visual C++에서 동일 하 게 작동 하는 코드의 경우 **`typename`** 선언에를 추가 합니다.

다음 샘플에서는 C4346를 생성 합니다.

```cpp
// C4346.cpp
// compile with: /WX /LD
template<class T>
struct C {
   T::X* x;   // C4346
   // try the following line instead
   // typename T::X* x;
};
```

다음 샘플에서는 키워드가 필요한 다른 예를 보여 줍니다 **`typename`** .

```cpp
// C4346b.cpp
// compile with: /LD /W1
template<class T>
const typename T::X& f(typename T::Z* p);   // Required in both places

template<class T, int N>
struct L{};

template<class T>
struct M : public L<typename T::Type, T::Value>
{   // required on type argument, not on non-type argument
   typedef typename T::X   Type;
   Type f();   // OK: "Type" is a type-specifer
   typename T::X g();   // typename required
   operator typename T::Z();   // typename required
};
```

그리고

```cpp
// C4346c.cpp
// compile with: /LD /WX
struct Y {
   typedef int Y_t;
};

template<class T>
struct A {
   typedef Y A_t;
};

template<class T>
struct B {
   typedef /*typename*/ A<T>::A_t B_t;   // C4346 typename needed here
   typedef /*typename*/ B_t::Y_t  B_t2;   // typename also needed here
};
```
