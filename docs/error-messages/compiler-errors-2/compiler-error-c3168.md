---
description: '자세한 정보: 컴파일러 오류 C3168'
title: 컴파일러 오류 C3168
ms.date: 11/04/2016
f1_keywords:
- C3168
helpviewer_keywords:
- C3168
ms.assetid: 4c36fcfb-c351-48ff-b4eb-78d2aa1b4d55
ms.openlocfilehash: a6b9708ebb9c7fe3d9d6be7d73c24b92b1e8c6eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242251"
---
# <a name="compiler-error-c3168"></a>컴파일러 오류 C3168

' type ': 열거형의 내부 형식이 잘못 되었습니다.

형식에 대해 지정한 기본 형식이 **`enum`** 잘못 되었습니다. 기본 형식은 정수 c + + 형식 또는 해당 CLR 형식 이어야 합니다.

다음 샘플에서는 C3168를 생성 합니다.

```cpp
// C3168.cpp
// compile with: /clr /c
ref class G{};

enum class E : G { e };   // C3168
enum class F { f };   // OK
```
