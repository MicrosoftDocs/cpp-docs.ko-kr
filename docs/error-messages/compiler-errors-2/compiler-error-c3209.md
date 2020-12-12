---
description: '자세한 정보: 컴파일러 오류 C3209'
title: 컴파일러 오류 C3209
ms.date: 11/04/2016
f1_keywords:
- C3209
helpviewer_keywords:
- C3209
ms.assetid: 1de44e39-69d1-4894-8f89-ff92136e8e5d
ms.openlocfilehash: 81b2453a8e6318c082d6cd8838cc4a384ba80517
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173924"
---
# <a name="compiler-error-c3209"></a>컴파일러 오류 C3209

' class ': 제네릭 클래스는 관리 되는 또는 WinRTclass 여야 합니다.

제네릭 클래스는 관리되는 클래스 또는 Windows 런타임 클래스여야 합니다.

다음 샘플에서는 C3209를 생성하고 해결 방법을 보여 줍니다.

```cpp
// C3209.cpp
// compile with: /clr
generic <class T>
class C {};   // C3209

// OK - ref class can be generic
generic <class T>
ref class D {};
```
