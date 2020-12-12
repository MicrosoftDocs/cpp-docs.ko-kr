---
description: '자세한 정보: 컴파일러 오류 C2787'
title: 컴파일러 오류 C2787
ms.date: 11/04/2016
f1_keywords:
- C2787
helpviewer_keywords:
- C2787
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
ms.openlocfilehash: 96a06908012e565bc606bf56f6a1709ee1f265a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297812"
---
# <a name="compiler-error-c2787"></a>컴파일러 오류 C2787

' identifier ':이 개체와 연결 된 GUID가 없습니다.

[__Uuidof](../../cpp/uuidof-operator.md) 연산자는 GUID가 연결 된 사용자 정의 형식 또는 사용자 정의 형식의 개체를 사용 합니다. 이 오류는 인수가 GUID가 없는 사용자 정의 형식인 경우에 발생 합니다.

다음 샘플에서는 C2787를 생성 합니다.

```cpp
// C2787.cpp
#include <windows.h>
struct F {};

struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) F2;

int main() {
   __uuidof(F);   // C2787
   __uuidof(F2);   // OK
}
```
