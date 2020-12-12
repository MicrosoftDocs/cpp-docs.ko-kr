---
description: '자세한 정보: 컴파일러 오류 C3368'
title: 컴파일러 오류 C3368
ms.date: 11/04/2016
f1_keywords:
- C3368
helpviewer_keywords:
- C3368
ms.assetid: 5bfd5be4-dfa9-4b33-9612-010561b40955
ms.openlocfilehash: 1b7fadb59bc0944b5092a235dfa0cb90c2233daa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150815"
---
# <a name="compiler-error-c3368"></a>컴파일러 오류 C3368

'function declaration': IDL에 대한 호출 규칙이 잘못되었습니다.

.idl 파일에서 [__stdcall](../../cpp/stdcall.md) 또는 [__cdecl](../../cpp/cdecl.md) 호출 규칙만 사용할 수 있습니다.

다음 샘플에서는 C3368을 생성합니다.

```cpp
// C3368.cpp
// processor: x86
[idl_module(name="Name", dllname="Some.dll")];

[idl_module(name="Name")]
int __fastcall f1();   // C3368
```
