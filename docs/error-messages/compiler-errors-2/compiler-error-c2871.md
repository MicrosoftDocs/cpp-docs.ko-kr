---
title: 컴파일러 오류 C2871
ms.date: 11/04/2016
f1_keywords:
- C2871
helpviewer_keywords:
- C2871
ms.assetid: 44aeb84d-61f0-45e0-8dad-22a3cd46b7f8
ms.openlocfilehash: 355a485de46916977be6f7b801794806a9c9e0ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492871"
---
# <a name="compiler-error-c2871"></a>컴파일러 오류 C2871

'name':이 이름의 네임 스페이스가 없습니다.

네임 스페이스를 하지 않은 식별자를 전달 하는 경우이 오류가 발생 한 [를 사용 하 여](../../cpp/namespaces-cpp.md#using_directives) 지시문입니다.

## <a name="example"></a>예제

다음 샘플에서는 C2871를 생성합니다.

```cpp
// C2871.cpp
// compile with: /c
namespace a {
   int fn(int i) { return i; }
}
namespace b {
   using namespace d;   // C2871 because d is not a namespace
   using namespace a;   // OK
}
```