---
description: '자세한 정보: 컴파일러 오류 C2504'
title: 컴파일러 오류 C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: 2a2269d750673a912096b497c10a9b112c23207c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213028"
---
# <a name="compiler-error-c2504"></a>컴파일러 오류 C2504

' class ': 기본 클래스를 정의 하지 않았습니다.

기본 클래스가 선언 되었지만 정의 되지 않았습니다.  가능한 원인:

1. 포함 파일이 없습니다.

1. 외부 기본 클래스가 [extern](../../cpp/extern-cpp.md)으로 선언 되지 않았습니다.

다음 샘플에서는 C2504를 생성 합니다.

```cpp
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

그래

```
class C{};
class D : public C {};
```
