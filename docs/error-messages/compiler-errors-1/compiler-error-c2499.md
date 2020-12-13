---
description: '자세한 정보: 컴파일러 오류 C2499'
title: 컴파일러 오류 C2499
ms.date: 11/04/2016
f1_keywords:
- C2499
helpviewer_keywords:
- C2499
ms.assetid: b323ff4d-b3c1-4bfd-b052-ae7292d53222
ms.openlocfilehash: 35d6c0017792c14b99418166af7ae6a84745340d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335087"
---
# <a name="compiler-error-c2499"></a>컴파일러 오류 C2499

' class ': 클래스는 자체 기본 클래스가 될 수 없습니다.

정의 하는 클래스를 기본 클래스로 지정 하려고 했습니다.

다음 샘플에서는 C2499를 생성 합니다.

```cpp
// C2499.cpp
// compile with: /c
class CMyClass : public CMyClass {};   // C2499
class CMyClass{};   // OK
```
