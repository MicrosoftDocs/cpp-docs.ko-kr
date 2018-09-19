---
title: 컴파일러 오류 C2502 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2502
dev_langs:
- C++
helpviewer_keywords:
- C2502
ms.assetid: affa0b86-15fc-4e17-b7f2-6aad4a3771c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5e3197ca71ff277f2904666261e7d0546a9128f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032533"
---
# <a name="compiler-error-c2502"></a>컴파일러 오류 C2502

'identifier': 기본 클래스의 액세스 한정자가 너무 많습니다

기본 클래스에 둘 이상의 액세스 한정자입니다. 하나의 액세스 한정자 (`public`하십시오 `private`, 또는 `protected`) 허용 됩니다.

다음 샘플에서는 C2502를 생성합니다.

```
// C2502.cpp
// compile with: /c
class A { };
class B { };
class C : private public A { };   // C2502

// OK
class D : private A {};
class E : public A, private B {};
```