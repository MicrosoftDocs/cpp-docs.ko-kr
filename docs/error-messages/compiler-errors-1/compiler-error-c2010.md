---
description: '자세한 정보: 컴파일러 오류 C2010'
title: 컴파일러 오류 C2010
ms.date: 11/04/2016
f1_keywords:
- C2010
helpviewer_keywords:
- C2010
ms.assetid: 5795ed1d-e206-410b-b7b4-528d125c67b4
ms.openlocfilehash: 8a96c30103d46c23f3b678a2fa84abf34445dd11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221035"
---
# <a name="compiler-error-c2010"></a>컴파일러 오류 C2010

' character ': 매크로 정식 매개 변수 목록에는 필요 하지 않습니다.

매크로 정의의 정식 매개 변수 목록에서 문자가 잘못 사용되었습니다. 오류를 해결 하려면 문자를 제거 합니다.

다음 샘플에서는 C2010를 생성 합니다.

```cpp
// C2010.cpp
// compile with: /c
#define mymacro(a|) (2*a)   // C2010
#define mymacro(a) (2*a)   // OK
```
