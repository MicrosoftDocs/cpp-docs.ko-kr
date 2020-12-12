---
description: '자세한 정보: 컴파일러 오류 C3385'
title: 컴파일러 오류 C3385
ms.date: 11/04/2016
f1_keywords:
- C3385
helpviewer_keywords:
- C3385
ms.assetid: 5f1838c1-986e-47db-8dbc-e06976b83cf3
ms.openlocfilehash: d51659561deb21882532b772455cf1e3636684aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285567"
---
# <a name="compiler-error-c3385"></a>컴파일러 오류 C3385

'class::function': DllImport 사용자 지정 특성을 가진 함수는 클래스의 인스턴스를 반환할 수 없습니다.

`DllImport` 특성으로 지정된 .dll 파일에 있는 것으로 정의된 함수는 클래스의 인스턴스를 반환할 수 없습니다.

다음 샘플에서는 C3385를 생성합니다.

```cpp
// C3385.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

struct SomeStruct1 {};

public ref struct Wrap {
   [ DllImport("somedll.dll", CharSet=CharSet::Unicode) ]
   static SomeStruct1 f1([In, Out] SomeStruct1 *pS);   // C3385
};
```
