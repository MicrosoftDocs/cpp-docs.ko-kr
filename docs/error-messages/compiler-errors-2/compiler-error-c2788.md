---
title: 컴파일러 오류 C2788 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2788
dev_langs:
- C++
helpviewer_keywords:
- C2788
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9a1464431d91e62ad07b4da0b3d1c8f9c13b243
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096212"
---
# <a name="compiler-error-c2788"></a>컴파일러 오류 C2788

'identifier':이 개체와 관련 된 둘 이상의 GUID

합니다 [__uuidof](../../cpp/uuidof-operator.md) 연산자 연결 된 GUID 또는 사용자 정의 형식의 개체를 사용 하 여 사용자 정의 형식을 사용 합니다. 이 오류는 인수는 여러 Guid 사용 하 여 개체인 경우에 발생 합니다.

다음 샘플에서는 C2788 오류가 생성 됩니다.

```
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