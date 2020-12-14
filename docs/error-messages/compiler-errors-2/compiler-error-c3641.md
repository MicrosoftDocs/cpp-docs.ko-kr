---
description: '자세한 정보: 컴파일러 오류 C3641'
title: 컴파일러 오류 C3641
ms.date: 11/04/2016
f1_keywords:
- C3641
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
ms.openlocfilehash: 391994a5207fe27cea0b33e6d03e5a1fdc30f6c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239105"
---
# <a name="compiler-error-c3641"></a>컴파일러 오류 C3641

> '*function*':/clr: pure 또는/clr: safe를 사용 하 여 컴파일된 함수에 대 한 호출 규칙 ' calling_convention '이 잘못 되었습니다.

## <a name="remarks"></a>설명

**/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

[/Clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)에서는 [__clrcall](../../cpp/clrcall.md) 호출 규칙만 사용할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3641를 생성 합니다.

```cpp
// C3641.cpp
// compile with: /clr:pure /c
void __cdecl f() {}   // C3641
```
