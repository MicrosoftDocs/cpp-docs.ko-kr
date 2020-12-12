---
description: '자세히 알아보기: 방법: gcnew를 사용 하 여 값 형식 만들기 및 암시적 Boxing 사용'
title: '방법: gcnew를 사용하여 값 형식 만들기 및 암시적 boxing 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- gcnew keyword [C++], creating value types
- boxing, implicit
- value types, creating
ms.assetid: ceb48841-d6bd-47be-a167-57f44c961603
ms.openlocfilehash: e58b50be4399cef6a842ce0b02e951617f143e5c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210896"
---
# <a name="how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing"></a>방법: gcnew를 사용하여 값 형식 만들기 및 암시적 boxing 사용

값 형식에 [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md) 를 사용 하면 boxed 값 형식이 생성 되 고,이 형식은 관리 되는 가비지 수집 힙에 배치 될 수 있습니다.

## <a name="example"></a>예제

```cpp
// vcmcppv2_explicit_boxing4.cpp
// compile with: /clr
public value class V {
public:
   int m_i;
   V(int i) : m_i(i) {}
};

public ref struct TC {
   void do_test(V^ v) {
      if (v != nullptr)
         ;
      else
         ;
   }
};

int main() {
   V^ v = gcnew V(42);
   TC^ tc = gcnew TC;
   tc->do_test(v);
}
```

## <a name="see-also"></a>참고 항목

[boxing](../extensions/boxing-cpp-component-extensions.md)
