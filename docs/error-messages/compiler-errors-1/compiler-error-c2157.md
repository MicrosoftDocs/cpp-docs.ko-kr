---
description: '자세한 정보: 컴파일러 오류 C2157'
title: 컴파일러 오류 C2157
ms.date: 11/04/2016
f1_keywords:
- C2157
helpviewer_keywords:
- C2157
ms.assetid: babbca24-16dc-4b69-be14-a675029249c1
ms.openlocfilehash: 4d8619d3d27bd9a1cb0c5323d9fdbf462b043ecf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181320"
---
# <a name="compiler-error-c2157"></a>컴파일러 오류 C2157

'function': pragma 목록에서 사용하려면 먼저 선언해야 합니다.

함수 이름이 선언되지 않은 상태에서 [alloc_text](../../preprocessor/alloc-text.md) pragma에 대한 함수 목록에서 참조되었습니다.

다음 샘플에서는 C2157을 생성합니다.

```cpp
// C2157.cpp
// compile with: /c
#pragma alloc_text( "func", func)   // C2157

// OK
extern "C" void func();
#pragma alloc_text( "func", func)
```
