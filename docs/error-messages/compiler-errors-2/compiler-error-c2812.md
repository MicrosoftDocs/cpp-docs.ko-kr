---
description: '자세한 정보: 컴파일러 오류 C2812'
title: 컴파일러 오류 C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: d59105397ae773c2a46b04a64eb50da3055c3a4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278426"
---
# <a name="compiler-error-c2812"></a>컴파일러 오류 C2812

> \#/clr: pure 및/clr: safe에서는 가져오기가 지원 되지 않습니다.

## <a name="remarks"></a>설명

**/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

**/clr: pure** 및 **/clr: safe** 에서는 네이티브 컴파일러 지원 라이브러리를 사용 해야 하므로 [#import 지시문](../../preprocessor/hash-import-directive-cpp.md) 은 지원 되지 않습니다 `#import` .

## <a name="example"></a>예제

다음 샘플에서는 C2812를 생성 합니다.

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```
