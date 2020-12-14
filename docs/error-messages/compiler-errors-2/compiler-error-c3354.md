---
description: '자세한 정보: 컴파일러 오류 C3354'
title: 컴파일러 오류 C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: cb2c110471b95010e56677608725e5d6abeaa5e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245319"
---
# <a name="compiler-error-c3354"></a>컴파일러 오류 C3354

'function': 대리자를 만드는 데 사용되는 함수는 'type' 반환 형식을 사용할 수 없습니다.

다음 형식은의 반환 형식으로 사용할 수 없습니다 **`delegate`** .

- 함수 포인터

- 멤버 포인터

- 멤버 함수에 대한 포인터

- 함수에 대한 참조

- 멤버 함수에 대한 참조

다음 샘플에서는 C3354를 생성합니다.

```cpp
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
