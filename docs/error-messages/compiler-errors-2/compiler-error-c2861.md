---
description: '자세한 정보: 컴파일러 오류 C2861'
title: 컴파일러 오류 C2861
ms.date: 11/04/2016
f1_keywords:
- C2861
helpviewer_keywords:
- C2861
ms.assetid: 012bb44d-6c9b-4def-b54e-b19f1f8ddd1b
ms.openlocfilehash: 82a4ed7d4b157bc141e9d437fa0f1d575759b48e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151127"
---
# <a name="compiler-error-c2861"></a>컴파일러 오류 C2861

' function name ': 인터페이스 멤버 함수를 정의할 수 없습니다.

컴파일러가 interface 키워드를 발견 했거나 구조체를 인터페이스로 추론 했지만 멤버 함수 정의를 찾았습니다.  인터페이스는 멤버 함수에 대 한 정의를 포함할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2861를 생성 합니다.

```cpp
// C2861.cpp
// compile with: /c
#include <objbase.h>   // required for IUnknown definition
[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IMyInterface : IUnknown {
   HRESULT mf(int a);
};

HRESULT IMyInterface::mf(int a) {}   // C2861
```
