---
description: '자세한 정보: 컴파일러 오류 C3196'
title: 컴파일러 오류 C3196
ms.date: 11/04/2016
f1_keywords:
- C3196
helpviewer_keywords:
- C3196
ms.assetid: d9c38a13-191d-472d-aa2b-f61a6459d16c
ms.openlocfilehash: 02ace9096754548a6629d1a5b5a71060a847da06
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241874"
---
# <a name="compiler-error-c3196"></a>컴파일러 오류 C3196

' keyword ': 두 번 이상 사용 되었습니다.

키워드가 두 번 이상 사용 되었습니다.

다음 샘플에서는 C3196를 생성 합니다.

```cpp
// C3196.cpp
// compile with: /clr
ref struct R abstract abstract {};   // C3196
ref struct S abstract {};   // OK
```
