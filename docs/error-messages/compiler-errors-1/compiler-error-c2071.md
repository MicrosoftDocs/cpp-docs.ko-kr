---
title: 컴파일러 오류 C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 7619d968379bfc35e98bd87071b75296d10c382c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743284"
---
# <a name="compiler-error-c2071"></a>컴파일러 오류 C2071

identifier': 스토리지 클래스가 잘못되었습니다

`identifier` 이 잘못 된 [저장소 클래스](../../c-language/c-storage-classes.md)를 사용 하 여 선언 되었습니다. 식별자에 대해 둘 이상의 스토리지 클래스를 지정하거나 정의가 스토리지 클래스 선언과 호환되지 않는 경우 이 오류가 발생할 수 있습니다.

이 문제를 해결 하려면 식별자의 의도 된 저장소 클래스 (예: 또는)를 이해 하 **`static`** **`extern`** 고 일치 하도록 선언을 수정 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2071 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C2071.cpp
// compile with: /c
struct C {
   extern int i;   // C2071
};
struct D {
   int i;   // OK, no extern on an automatic
};
```

다음 샘플에서는 C2071 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```
