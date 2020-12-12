---
description: '자세한 정보: 컴파일러 오류 C2160'
title: 컴파일러 오류 C2160
ms.date: 11/04/2016
f1_keywords:
- C2160
helpviewer_keywords:
- C2160
ms.assetid: a1f694a7-fb16-4437-b7f5-a1af6da94bc5
ms.openlocfilehash: 84c257fc249d136c495adbcb22cd59701d6c363c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181191"
---
# <a name="compiler-error-c2160"></a>컴파일러 오류 C2160

매크로 정의 시작에 '##'이 올 수 없습니다.

매크로 정의가 토큰 붙여넣기 연산자(##)로 시작되었습니다.

다음 샘플에서는 C2160을 생성합니다.

```cpp
// C2160.cpp
// compile with: /c
#define mac(a,b) #a   // OK
#define mac(a,b) ##a   // C2160
```
