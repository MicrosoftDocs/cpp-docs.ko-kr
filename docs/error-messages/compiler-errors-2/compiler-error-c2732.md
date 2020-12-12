---
description: '자세한 정보: 컴파일러 오류 C2732'
title: 컴파일러 오류 C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 1ca97fbf46685af1df37b8caf82a03effc1ec6bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123216"
---
# <a name="compiler-error-c2732"></a>컴파일러 오류 C2732

링크 사양이 'function'에 대한 초기 사양과 모순됩니다.

함수가 다른 링크 지정자를 사용하여 이미 선언되었습니다.

이 오류는 링크 지정자가 다른 포함 파일로 인해 발생할 수 있습니다.

이 오류를 해결 하려면 연결이 일치 하도록 문을 변경 합니다 **`extern`** . 특히 `extern "C"` 블록에서 `#include` 지시문을 줄 바꿈하지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2732를 생성합니다.

```cpp
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```
