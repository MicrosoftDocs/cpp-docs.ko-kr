---
description: '자세한 정보: 컴파일러 오류 C2788'
title: 컴파일러 오류 C2788
ms.date: 11/04/2016
f1_keywords:
- C2788
helpviewer_keywords:
- C2788
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
ms.openlocfilehash: 8521df743e6c19f250d0344d4adf2299934887e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297787"
---
# <a name="compiler-error-c2788"></a>컴파일러 오류 C2788

' identifier ':이 개체와 연결 된 GUID가 두 개 이상입니다.

[__Uuidof](../../cpp/uuidof-operator.md) 연산자는 GUID가 연결 된 사용자 정의 형식 또는 사용자 정의 형식의 개체를 사용 합니다. 인수가 여러 Guid 인 개체인 경우이 오류가 발생 합니다.

다음 샘플에서는 C2788를 생성 합니다.

```cpp
// C2788.cpp
#include <windows.h>
struct __declspec(uuid("00000001-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000002-0000-0000-0000-000000000000}")) B {};
template <class T, class U> class MyClass {};

typedef MyClass<A,B> MyBadClass;
typedef MyClass<A,A> MyGoodClass;

int main() {
   __uuidof(MyBadClass);    // C2788
   // try the following line instead
   __uuidof(MyGoodClass);
}
```
