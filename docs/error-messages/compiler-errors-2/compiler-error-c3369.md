---
title: 컴파일러 오류 C3369
ms.date: 11/04/2016
f1_keywords:
- C3369
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
ms.openlocfilehash: 3b2e6f38e93514154b20e674139a2d771dcf586e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503243"
---
# <a name="compiler-error-c3369"></a>컴파일러 오류 C3369

'module name': idl_module이 이미 정의되었습니다.

DLL을 정의하는 [idl_module](../../windows/attributes/idl-module.md) 사용은 프로그램에서 한 번만 발생할 수 있습니다.

다음 샘플에서는 C3369를 생성합니다.

```cpp
// C3369.cpp
// compile with: /c
[idl_module(name="name1", dllname="x.dll")]; // C3369
[idl_module(name="name1", dllname="x.dll")];
```
