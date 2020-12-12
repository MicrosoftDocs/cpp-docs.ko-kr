---
description: '자세한 정보: 컴파일러 오류 C2633'
title: 컴파일러 오류 C2633
ms.date: 11/04/2016
f1_keywords:
- C2633
helpviewer_keywords:
- C2633
ms.assetid: a7aceb65-4255-42d6-a8fb-e3cb6c4d2270
ms.openlocfilehash: 182cafdd9a79744414a89792e1361c8173077705
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123450"
---
# <a name="compiler-error-c2633"></a>컴파일러 오류 C2633

' identifier ': ' inline '은 생성자에 대해 유일 하 게 올바른 저장소 클래스입니다.

생성자는 인라인이 아닌 저장소 클래스로 선언 됩니다.

다음 샘플에서는 C2633를 생성 합니다.

```cpp
// C2633.cpp
// compile with: /c
class C {
   extern C();   // C2633, not inline
   inline C();   // OK
};
```
