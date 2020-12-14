---
description: '자세한 정보: 컴파일러 오류 C3896'
title: 컴파일러 오류 C3896
ms.date: 11/04/2016
f1_keywords:
- C3896
helpviewer_keywords:
- C3896
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
ms.openlocfilehash: c08a9af6d10e741b39fa2547cfbc6c04a6dd3a1a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222699"
---
# <a name="compiler-error-c3896"></a>컴파일러 오류 C3896

' member ': 잘못 된 이니셜라이저:이 리터럴 데이터 멤버는 ' nullptr '로만 초기화할 수 있습니다.

[리터럴](../../extensions/literal-cpp-component-extensions.md) 데이터 멤버가 잘못 초기화 되었습니다.  자세한 내용은 [nullptr](../../extensions/nullptr-cpp-component-extensions.md) 를 참조 하세요.

다음 샘플에서는 C3896를 생성 합니다.

```cpp
// C3896.cpp
// compile with: /clr /c
ref class R{};

value class V {
   literal R ^ r = "test";   // C3896
   literal R ^ r2 = nullptr;   // OK
};
```
