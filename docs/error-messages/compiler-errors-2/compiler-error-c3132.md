---
description: '자세한 정보: 컴파일러 오류 C3132'
title: 컴파일러 오류 C3132
ms.date: 11/04/2016
f1_keywords:
- C3132
helpviewer_keywords:
- C3132
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
ms.openlocfilehash: e81ddcb977342a687dce329239a590f90eca67ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177395"
---
# <a name="compiler-error-c3132"></a>컴파일러 오류 C3132

' function-parameter ': 매개 변수 배열은 ' 단일 차원 관리 되는 배열 ' 형식의 형식 인수에만 적용할 수 있습니다.

<xref:System.ParamArrayAttribute>단일 차원 배열이 아닌 매개 변수에 특성이 적용 되었습니다.

다음 샘플에서는 C3132를 생성 합니다.

```cpp
// C3132.cpp
// compile with: /clr /c
using namespace System;
void f( [ParamArray] Int32[,] );   // C3132
void g( [ParamArray] Int32[] );   // C3132

void h( [ParamArray] array<Char ^> ^ MyArray );   // OK
```
