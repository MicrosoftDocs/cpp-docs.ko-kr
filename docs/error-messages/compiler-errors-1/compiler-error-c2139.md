---
description: '자세한 정보: 컴파일러 오류 C2139'
title: 컴파일러 오류 C2139
ms.date: 11/04/2016
f1_keywords:
- C2139
helpviewer_keywords:
- C2139
ms.assetid: 31e047c0-5bf9-46c2-b6de-b627ea6a5768
ms.openlocfilehash: 240d1cdd4144e77a31063985a8a1fffb6992196c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323066"
---
# <a name="compiler-error-c2139"></a>컴파일러 오류 C2139

' type ': 정의 되지 않은 클래스는 컴파일러 내장 형식 특성 ' 특성 '에 대 한 인수로 사용할 수 없습니다.

잘못 된 인수가 형식 특성에 전달 되었습니다.

자세한 내용은 [형식 특성에 대한 컴파일러 지원](../../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2139를 생성 합니다.

```cpp
// C2139.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class C;
class D {};

class E {
public:
   virtual void Test() {}
};

int main() {
   cout << is_polymorphic<C>::value << endl;   // C2139
   cout << is_polymorphic<D>::value << endl;   // OK
   cout << is_polymorphic<E>::value << endl;   // OK
}
```
