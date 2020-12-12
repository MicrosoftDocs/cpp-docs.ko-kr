---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4290'
title: 컴파일러 경고(수준 3) C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: 771eb01c23778a716aee22ca747ea6473909a8bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344070"
---
# <a name="compiler-warning-level-3-c4290"></a>컴파일러 경고(수준 3) C4290

함수가 __declspec 되지 않았음을 나타내는 경우를 제외 하 고 c + + 예외 사양이 무시 됨 (nothrow)

함수는 예외 사양을 사용 하 여 선언 되며,이는 Visual C++ 허용 하지만 구현 하지는 않습니다. 컴파일 중에 무시 되는 예외 사양을 사용 하는 코드는 나중에 예외 사양을 지 원하는 버전에서 다시 사용 하도록 다시 컴파일하거나 연결 해야 할 수 있습니다.

자세한 내용은 [예외 사양 (throw)](../../cpp/exception-specifications-throw-cpp.md) 을 참조 하세요.

[경고](../../preprocessor/warning.md) pragma를 사용 하 여이 경고를 방지할 수 있습니다.

```cpp
#pragma warning( disable : 4290 )
```

다음 코드 샘플에서는 C4290를 생성 합니다.

```cpp
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```
