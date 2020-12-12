---
description: '자세한 정보: 컴파일러 오류 C2909'
title: 컴파일러 오류 C2909
ms.date: 11/04/2016
f1_keywords:
- C2909
helpviewer_keywords:
- C2909
ms.assetid: 1c9df8ae-925d-4002-a5f8-a71413c45f9e
ms.openlocfilehash: c2a3ba74f87edb0f1958910d04820316508f6567
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270643"
---
# <a name="compiler-error-c2909"></a>컴파일러 오류 C2909

'identifier': 함수 템플릿을 명시적으로 인스턴스화하려면 반환 형식이 있어야 합니다.

함수 템플릿의 명시적으로 인스턴스화하려면 해당 반환 형식의 명시적 사양이 있어야 합니다. 암시적 반환 형식 사양은 작동하지 않습니다.

다음 샘플에서는 C2909를 생성합니다.

```cpp
// C2909.cpp
// compile with: /c
template<class T> int f(T);
template f<int>(int);         // C2909
template int f<int>(int);   // OK
```
