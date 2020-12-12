---
description: '자세한 정보: 컴파일러 오류 C3816'
title: 컴파일러 오류 C3816
ms.date: 11/04/2016
f1_keywords:
- C3816
helpviewer_keywords:
- C3816
ms.assetid: 2e52cc7f-e31c-41a3-8d6f-9f5fab3648c0
ms.openlocfilehash: b2a4ffc435ad4fc2e0c516d99ade1058799fb4b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180957"
---
# <a name="compiler-error-c3816"></a>컴파일러 오류 C3816

' i n t '는 이전에 다른 관리 또는 WinRTmodifier로 선언 되었거나 정의 되었습니다.

정방향 선언 및 실제 선언에서는 특성의 선언에 충돌이나 불일치가 없어야 합니다.

다음 샘플에서는 C3816을 생성하고 해결 방법을 보여 줍니다.

```cpp
// C3816a.cpp
// compile with: /clr /c
class C1;
// try the following line instead
// ref class C1;

ref class C1{  // C3816, forward declaration does not use ref
};
```
