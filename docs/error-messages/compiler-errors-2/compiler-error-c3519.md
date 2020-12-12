---
description: '자세한 정보: 컴파일러 오류 C3519'
title: 컴파일러 오류 C3519
ms.date: 11/04/2016
f1_keywords:
- C3519
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
ms.openlocfilehash: f8eb90620894627beab450275c6725d665d837e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113090"
---
# <a name="compiler-error-c3519"></a>컴파일러 오류 C3519

' invalid_param ': embedded_idl 특성에 대 한 매개 변수가 잘못 되었습니다.

매개 변수가 `embedded_idl` [#import](../../preprocessor/hash-import-directive-cpp.md)의 특성에 전달 되었지만 컴파일러가 매개 변수를 인식 하지 못했습니다.

에 대해 허용 되는 유일한 매개 변수는 `embedded_idl` `emitidl` 및 `no_emitidl` 입니다.

다음 샘플에서는 C3519를 생성 합니다.

```cpp
// C3519.cpp
// compile with: /LD
[module(name="MyLib2")];
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")
// C3519
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")
// OK
```
