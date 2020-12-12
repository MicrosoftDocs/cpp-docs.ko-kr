---
description: '자세한 정보: 컴파일러 오류 C2518'
title: 컴파일러 오류 C2518
ms.date: 11/04/2016
f1_keywords:
- C2518
helpviewer_keywords:
- C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
ms.openlocfilehash: 1ebc270cd3544dc50d051677faeeec8e8e6bd979
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212729"
---
# <a name="compiler-error-c2518"></a>컴파일러 오류 C2518

기본 클래스 목록에 ' keyword ' 키워드가 잘못 되었습니다. 무시

및 키워드 **`class`** 는 **`struct`** 기본 클래스 목록에 표시 되지 않아야 합니다.

다음 샘플에서는 C2518를 생성 합니다.

```cpp
// C2518.cpp
// compile with: /c
class B {};
class C : public class B {};   // C2518
class D: public B {};   // OK
```
