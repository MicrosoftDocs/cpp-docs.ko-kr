---
title: 컴파일러 경고 C4986 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4986
dev_langs:
- C++
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f464f2a6e1f76c7d8b9de8bcc2353766aff0854
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077063"
---
# <a name="compiler-warning-c4986"></a>컴파일러 경고 C4986

'function': 예외 사양이 이전 선언과 일치하지 않습니다.

이 경고는 하나의 선언에 예외 사양이 있고 다른 선언에는 없는 경우에 발생할 수 있습니다.

기본적으로 C4986은 해제되어 있습니다. 자세한 내용은 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플 C4986를 생성합니다.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1()
{
    // ...
}
```

## <a name="example"></a>예제

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