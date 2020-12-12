---
description: '자세한 정보: 컴파일러 오류 C3216'
title: 컴파일러 오류 C3216
ms.date: 11/04/2016
f1_keywords:
- C3216
helpviewer_keywords:
- C3216
ms.assetid: bbab1efe-8779-4489-8bb0-b11e45f5cbe5
ms.openlocfilehash: 0f7ea3950b4fb832bdb349e788fbd73309918dd3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173729"
---
# <a name="compiler-error-c3216"></a>컴파일러 오류 C3216

제약 조건은 'type'이 아니라 제네릭 매개 변수여야 합니다.

제약 조건 형식이 잘못되었습니다.

다음 샘플에서는 C3216을 생성합니다.

```cpp
// C3216.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where F : A   // C3216
// Try the following line instead:
// where T : A    // C3216
ref class C {};
```

다음 예제에서는 가능한 해결 방법을 설명합니다.

```cpp
// C3216b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
where T : A
ref class C {};
```
