---
description: '자세한 정보: 컴파일러 오류 C2165'
title: 컴파일러 오류 C2165
ms.date: 11/04/2016
f1_keywords:
- C2165
helpviewer_keywords:
- C2165
ms.assetid: b108313b-b8cb-4dce-b2ec-f2b31c9cdc87
ms.openlocfilehash: 6c019a1f2fe9edd92d1ebd57b67fd65da262accf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274634"
---
# <a name="compiler-error-c2165"></a>컴파일러 오류 C2165

'keyword': 데이터에 대한 포인터를 수정할 수 없습니다.

**`__stdcall`**, **`__cdecl`** 또는 **`__fastcall`** 키워드가 데이터에 대 한 포인터를 수정 하려고 합니다.

다음 샘플에서는 C2165를 생성합니다.

```cpp
// C2165.cpp
// compile with: /c
char __cdecl *p;   // C2165
char *p;   // OK
```
