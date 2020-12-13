---
description: '자세한 정보: 컴파일러 오류 C2238'
title: 컴파일러 오류 C2238
ms.date: 11/04/2016
f1_keywords:
- C2238
helpviewer_keywords:
- C2238
ms.assetid: 3d53060c-d6b7-4603-b9cf-d7c65eb64cd2
ms.openlocfilehash: 90c5eb840c300aa18b06f49a7e160c6cb7bd8e9e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338749"
---
# <a name="compiler-error-c2238"></a>컴파일러 오류 C2238

'token' 앞에 예기치 않은 토큰이 있습니다.

잘못된 토큰이 있습니다.

다음 샘플에서는 C2238을 생성합니다.

```cpp
// C2238.cpp
// compile with: /c
class v {
virtual: int vvv;   // C2238
};
```
