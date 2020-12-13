---
description: '자세한 정보: 컴파일러 오류 C2860'
title: 컴파일러 오류 C2860
ms.date: 11/04/2016
f1_keywords:
- C2860
helpviewer_keywords:
- C2860
ms.assetid: ccc83553-90ed-4e94-b5e9-38b58ae38e31
ms.openlocfilehash: 27474577e31cdc046769f9fc26686d3aaa7f3e64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341167"
---
# <a name="compiler-error-c2860"></a>컴파일러 오류 C2860

' void '는 ' (void) '를 제외한 인수 형식일 수 없습니다.

형식은 **`void`** 다른 인수를 사용 하는 인수 형식으로 사용할 수 없습니다.

다음 샘플에서는 C2860를 생성 합니다.

```cpp
// C2860.cpp
// compile with: /c
void profunc1(void, int i);   // C2860
void func10(void);   // OK
```
