---
title: 컴파일러 경고 (수준 1) C4042 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4042
dev_langs:
- C++
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bef2071cf31123b5b172df2651c0d6a6d87d4fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067477"
---
# <a name="compiler-warning-level-1-c4042"></a>컴파일러 경고 (수준 1) C4042

'identifier': 저장소 클래스가 잘못 되었습니다

이 컨텍스트에서이 식별자를 사용 하 여 지정 된 저장소 클래스를 사용할 수 없습니다. 컴파일러는 기본 저장소 클래스를 대신 사용 합니다.

- `extern`를 하는 경우 *식별자* 함수입니다.

- **자동**이면 *식별자* 정식 매개 변수 또는 지역 변수입니다.

- 하는 경우 저장소 클래스 *식별자* 전역 변수입니다.

이외의 다른 저장소 클래스를 지정 하 여이 경고를 발생할 수 있습니다 **등록** 매개 변수 선언에 있습니다.

다음 샘플에서는 C4042

```
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```