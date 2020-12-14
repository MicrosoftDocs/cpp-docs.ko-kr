---
description: '자세한 정보: 컴파일러 경고 C 4936'
title: 컴파일러 경고 C4936
ms.date: 11/04/2016
f1_keywords:
- C4936
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
ms.openlocfilehash: e12cb789d3d008ec61672591cde78f1b7dc61da6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314986"
---
# <a name="compiler-warning-c4936"></a>컴파일러 경고 C4936

> /clr 또는 /clr:pure를 지정하여 컴파일한 경우에만 이 __declspec를 사용할 수 있습니다.

## <a name="remarks"></a>설명

**/Clr: pure** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

**`__declspec`** 한정자가 사용 되었지만 해당 **`__declspec`** 한정자는 [/clr](../../build/reference/clr-common-language-runtime-compilation.md) 옵션 중 하나로 컴파일된 경우에만 유효 합니다.

자세한 내용은 [appdomain](../../cpp/appdomain.md) 및 [process](../../cpp/process.md)를 참조하세요.

C4936은 항상 오류로 실행됩니다.  [warning](../../preprocessor/warning.md) pragma를 사용하여 C4936을 해제할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4936을 생성합니다.

```cpp
// C4936.cpp
// compile with: /c
// #pragma warning (disable : 4936)
__declspec(process) int i;   // C4936
__declspec(appdomain) int j;   // C4936
```
