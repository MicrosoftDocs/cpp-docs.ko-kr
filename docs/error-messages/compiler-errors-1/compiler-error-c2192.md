---
description: '자세한 정보: 컴파일러 오류 C2192'
title: 컴파일러 오류 C2192
ms.date: 11/04/2016
f1_keywords:
- C2192
helpviewer_keywords:
- C2192
ms.assetid: a147197e-e72d-4620-939b-f9e08d7c7c12
ms.openlocfilehash: 02b1b5ace60d2b9a288cf933a43c5603b734eac7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337677"
---
# <a name="compiler-error-c2192"></a>컴파일러 오류 C2192

' number ' 매개 변수 선언이 다릅니다.

다른 매개 변수 목록을 사용 하 여 C 함수를 두 번 선언 했습니다. C는 오버 로드 된 함수를 지원 하지 않습니다.

다음 샘플에서는 C2192를 생성 합니다.

```c
// C2192.c
// compile with: /Za /c
void func( float, int );
void func( int, float );   // C2192, different parameter list
void func2( int, float );   // OK
```
