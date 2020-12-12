---
description: '자세한 정보: 컴파일러 오류 C2337'
title: 컴파일러 오류 C2337
ms.date: 09/19/2019
f1_keywords:
- C2337
helpviewer_keywords:
- C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
ms.openlocfilehash: 44def6fe9c220699e3687ce9b843f977528b5e15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234854"
---
# <a name="compiler-error-c2337"></a>컴파일러 오류 C2337

> '*attribute-name*': 특성을 찾을 수 없습니다.

코드가이 컨텍스트에서 지원 되지 않는 특성을 사용 합니다. 또는이 버전의 컴파일러에서는 특성을 사용할 수 없습니다. 이 문제를 해결 하려면 지원 되지 않는 특성을 제거 합니다.

다음 샘플에서는 C2337을 생성합니다.

```cpp
// C2337.cpp
// compile with: /c
[emitidl];
[module(name="x")];
[grasshopper]   // C2337, not a supported attribute
class a{};
```
