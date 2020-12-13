---
description: '자세한 정보: 컴파일러 오류 C3347'
title: 컴파일러 오류 C3347
ms.date: 11/04/2016
f1_keywords:
- C3347
helpviewer_keywords:
- C3347
ms.assetid: e939ad29-0b78-4681-9618-9bdae5675cee
ms.openlocfilehash: b7703865af7b081c362c110e07c2b1d3d8471129
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144562"
---
# <a name="compiler-error-c3347"></a>컴파일러 오류 C3347

'arg': idl_module 특성에 필수 인수를 지정하지 않았습니다.

필수 인수가 [idl_module](../../windows/attributes/idl-module.md) 특성에 전달되지 않았습니다.

다음 샘플에서는 C3347을 생성합니다.

```cpp
// C3347.cpp
// compile with: /c
[module(name="xx")];

[idl_module(dllname="x")];    // C3347
// try the following line instead
// [idl_module(name="test", dllname="x")];
```
