---
title: 컴파일러 오류 C3369 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3369
dev_langs:
- C++
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b111889c6a4203f5b63a7a644adbc7a51d8a810a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018005"
---
# <a name="compiler-error-c3369"></a>컴파일러 오류 C3369

'module name': idl_module이 이미 정의되었습니다.

DLL을 정의하는 [idl_module](../../windows/idl-module.md) 사용은 프로그램에서 한 번만 발생할 수 있습니다.

다음 샘플에서는 C3369를 생성합니다.

```
// C3369.cpp
// compile with: /c
[idl_module(name="name1", dllname="x.dll")]; // C3369
[idl_module(name="name1", dllname="x.dll")];
```