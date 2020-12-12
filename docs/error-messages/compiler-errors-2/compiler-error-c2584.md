---
description: '자세한 정보: 컴파일러 오류 C2584'
title: 컴파일러 오류 C2584
ms.date: 11/04/2016
f1_keywords:
- C2584
helpviewer_keywords:
- C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
ms.openlocfilehash: 7820019c3ec49928f59980adbd9ec814d67c3499
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177681"
---
# <a name="compiler-error-c2584"></a>컴파일러 오류 C2584

' Class ': 직접 기본 ' Base2 '에 액세스할 수 없습니다. 이미 ' Base1 '의 기본입니다.

`Class` 는 이미에서 직접 파생 `Base1` 됩니다. `Base2` 도에서 파생 `Base1` 됩니다. `Class``Base2`은 (는)를 다시 상속 (간접적으로) 한다는 것을 의미 하므로는에서 파생 될 수 없습니다 `Base1` `Base1` .이는 이미 직접 기본 클래스 이므로 유효 하지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2584를 생성 합니다.

```cpp
// C2584.cpp
// compile with: /c
struct A1 {
   virtual int MyFunction();
};

struct A2 {
    virtual int MyFunction();
};

struct B1: public virtual A1, virtual A2 {
    virtual int MyFunction();
};

struct B2: public virtual A2, virtual A1 {
    virtual int MyFunction();
};

struct C: virtual B1, B2 {
    virtual int MyFunction();
};

struct Z : virtual B2, virtual C {   // C2584
// try the following line insted
// struct Z : virtual C {
    virtual int MyFunction();
};
```
