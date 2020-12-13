---
description: '자세한 정보: 컴파일러 오류 C2523'
title: 컴파일러 오류 C2523
ms.date: 11/04/2016
f1_keywords:
- C2523
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
ms.openlocfilehash: c9907742903cf4c13364d6ac63bb561b52e02232
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151166"
---
# <a name="compiler-error-c2523"></a>컴파일러 오류 C2523

' class:: ~ identifier ': 소멸자/종료자 태그가 일치 하지 않습니다.

소멸자의 이름은 클래스 이름 앞에 물결표 ()가와 야 합니다 `~` . 생성자와 소멸자는 클래스와 동일한 이름을 가진 유일한 멤버입니다.

다음 샘플에서는 C2523를 생성 합니다.

```cpp
// C2523.cpp
// compile with: /c
class A {
   ~B();    // C2523
   ~A();   // OK
};
```
