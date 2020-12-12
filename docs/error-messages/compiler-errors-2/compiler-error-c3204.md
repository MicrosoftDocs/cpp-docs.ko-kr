---
description: '자세한 정보: 컴파일러 오류 C3204'
title: 컴파일러 오류 C3204
ms.date: 11/04/2016
f1_keywords:
- C3204
helpviewer_keywords:
- C3204
ms.assetid: 06e578da-0262-48c8-b2ae-be1cd6d28884
ms.openlocfilehash: 8e9275cada58988c9dac3942569fb0416ddff0ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285736"
---
# <a name="compiler-error-c3204"></a>컴파일러 오류 C3204

'_alloca'는 catch 블록 내부에서 호출할 수 없습니다.

이 오류는 catch 블록 내에서 [_alloca](../../c-runtime-library/reference/alloca.md) 호출을 사용하는 경우에 발생합니다.

## <a name="example"></a>예제

다음 샘플에서는 C3204를 생성합니다.

```cpp
// C3204.cpp
// compile with: /EHsc
#include <malloc.h>

void ShowError(void)
{
   try
   {
   }
   catch(...)
   {
      _alloca(1);   // C3204
   }
}
```
