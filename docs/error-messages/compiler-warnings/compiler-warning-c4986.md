---
title: 컴파일러 경고 C4986
ms.date: 11/04/2016
f1_keywords:
- C4986
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
ms.openlocfilehash: ae782ea0a11bd72c867ea9532a62d0b14cd98453
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684394"
---
# <a name="compiler-warning-c4986"></a>컴파일러 경고 C4986

'function': 예외 사양이 이전 선언과 일치하지 않습니다.

이 경고는 하나의 선언에 예외 사양이 있고 다른 선언에는 없는 경우에 발생할 수 있습니다.

기본적으로 C4986은 해제되어 있습니다. 자세한 내용은 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)을 참조하세요.

## <a name="examples"></a>예제

다음 샘플에서는 C4986를 생성 합니다.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1()
{
    // ...
}
```

다음 샘플 코드에서는 이 경고를 제거합니다.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1() throw (X*)
{
    // ...
}
```
