---
description: '자세한 정보: 컴파일러 오류 C2341'
title: 컴파일러 오류 C2341
ms.date: 11/04/2016
f1_keywords:
- C2341
helpviewer_keywords:
- C2341
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
ms.openlocfilehash: 47869b6534664358fa80a3ace89fc44fdceefb08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234789"
---
# <a name="compiler-error-c2341"></a>컴파일러 오류 C2341

' section name ': 세그먼트를 사용 하려면 먼저 #pragma data_seg, code_seg 또는 섹션을 사용 하 여 세그먼트를 정의 해야 합니다.

대입문은 [code_seg](../../preprocessor/code-seg.md), [data_seg](../../preprocessor/data-seg.md)또는 [section](../../preprocessor/section.md) pragma가 아직 정의 [하지 않은 세그먼트](../../cpp/allocate.md) 를 참조 합니다.

다음 샘플에서는 C2341를 생성 합니다.

```cpp
// C2341.cpp
// compile with: /c
__declspec(allocate(".test"))   // C2341
int j = 1;
```

해결 방법:

```cpp
// C2341b.cpp
// compile with: /c
#pragma data_seg(".test")
__declspec(allocate(".test"))
int j = 1;
```
