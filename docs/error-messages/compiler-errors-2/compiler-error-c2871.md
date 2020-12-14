---
description: '자세한 정보: 컴파일러 오류 C2871'
title: 컴파일러 오류 C2871
ms.date: 11/04/2016
f1_keywords:
- C2871
helpviewer_keywords:
- C2871
ms.assetid: 44aeb84d-61f0-45e0-8dad-22a3cd46b7f8
ms.openlocfilehash: 6b62d5decb67cf6f8bad4d9b30123ccab54f51c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198299"
---
# <a name="compiler-error-c2871"></a>컴파일러 오류 C2871

' name ':이 이름을 가진 네임 스페이스가 없습니다.

이 오류는 네임 스페이스가 아닌 식별자를 [using](../../cpp/namespaces-cpp.md#using_directives) 지시문에 전달할 때 발생 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2871를 생성 합니다.

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
