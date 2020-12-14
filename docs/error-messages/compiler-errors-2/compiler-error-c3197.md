---
description: '자세한 정보: 컴파일러 오류 C3197'
title: 컴파일러 오류 C3197
ms.date: 11/04/2016
f1_keywords:
- C3197
helpviewer_keywords:
- C3197
ms.assetid: 4e385c3b-222e-425c-9612-46e83ed41650
ms.openlocfilehash: f03792a2dd5120ed2b4a05b2110186d5c985e502
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203759"
---
# <a name="compiler-error-c3197"></a>컴파일러 오류 C3197

' keyword ': 정의 에서만 사용할 수 있습니다.

키워드는 선언에서 사용 되었지만 정의 에서만 유효 합니다.

다음 샘플에서는 C3197를 생성 합니다.

```cpp
// C3197.cpp
// compile with: /clr /c
ref struct R abstract;   // C3197
ref struct R abstract {};   // OK

public ref class MyObject;   // C3197
ref class MyObject;   // OK
public ref class MyObject {};   // OK
```
