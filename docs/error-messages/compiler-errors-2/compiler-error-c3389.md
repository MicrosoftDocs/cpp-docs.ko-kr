---
description: '자세한 정보: 컴파일러 오류 C3389'
title: 컴파일러 오류 C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: b9fedf0993738d054cd5ded605d96001b3db13eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285502"
---
# <a name="compiler-error-c3389"></a>컴파일러 오류 C3389

> /clr: pure 또는/clr: safe에는 __declspec (*키워드*)를 사용할 수 없습니다.

## <a name="remarks"></a>설명

**`/clr:pure`** 및 **`/clr:safe`** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

[`__declspec`](../../cpp/declspec.md)사용 되는 한정자는 프로세스별 상태를 의미 합니다.  [`/clr:pure`](../../build/reference/clr-common-language-runtime-compilation.md) 는 상태를 나타냅니다 [`appdomain`](../../cpp/appdomain.md) .  따라서 *키워드* 한정자를 사용 하 여 변수를 선언 **`__declspec`** 하 고로 컴파일하는 것은 **`/clr:pure`** 허용 되지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3389를 생성 합니다.

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
