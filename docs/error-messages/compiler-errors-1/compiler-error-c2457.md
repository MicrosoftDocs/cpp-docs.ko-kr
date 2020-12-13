---
description: '자세한 정보: 컴파일러 오류 C2457'
title: 컴파일러 오류 C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: 1fea5192b97e280a38f674a67b0bf739041ffe97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332366"
---
# <a name="compiler-error-c2457"></a>컴파일러 오류 C2457

> '*macro*': 미리 정의 된 매크로는 함수 본문 외부에 나타날 수 없습니다.

[&#95;&#95;함수&#95;&#95;](../../preprocessor/predefined-macros.md)같은 미리 정의 된 매크로를 전역 공간에 사용 하려고 했습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2457를 생성 하 고 올바른 사용법도 보여 줍니다.

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```
