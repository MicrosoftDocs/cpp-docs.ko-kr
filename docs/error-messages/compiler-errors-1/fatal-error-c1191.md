---
description: '자세한 정보: 심각한 오류 C1191'
title: 심각한 오류 C1191
ms.date: 11/04/2016
f1_keywords:
- C1191
helpviewer_keywords:
- C1191
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
ms.openlocfilehash: ef7f9ec6554daf0d83f3e597877509025512a6d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123580"
---
# <a name="fatal-error-c1191"></a>심각한 오류 C1191

' d l l '은 전역 범위 에서만 가져올 수 있습니다.

/Clr 프로그래밍을 사용 하는 프로그램에 mscorlib.dll를 가져오는 명령은 네임 스페이스나 함수에 표시 될 수 없지만 전역 범위에는 표시 되어야 합니다.

다음 샘플에서는 C1191를 생성 합니다.

```cpp
// C1191.cpp
// compile with: /clr
namespace sample {
   #using <mscorlib.dll>   // C1191 not at global scope
}
```

해결 방법:

```cpp
// C1191b.cpp
// compile with: /clr /c
#using <mscorlib.dll>
namespace sample {}
```
