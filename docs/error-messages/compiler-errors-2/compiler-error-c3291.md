---
title: 컴파일러 오류 C3291
ms.date: 11/04/2016
f1_keywords:
- C3291
helpviewer_keywords:
- C3291
ms.assetid: ed2e9f89-8dbc-4387-bc26-cc955e840858
ms.openlocfilehash: 6d9602d1ec9f2e4a72784e20bfd90c7f3aac0781
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611343"
---
# <a name="compiler-error-c3291"></a>컴파일러 오류 C3291

'default' : trivial 속성의 이름이 될 수 없습니다.

trivial 속성은 `default`로 이름을 바꿀 수 없습니다. 자세한 내용은 [property](../../windows/property-cpp-component-extensions.md) 를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3291을 생성합니다.

```
// C3291.cpp
// compile with: /clr /c
ref struct C {
   property System::String ^ default;   // C3291
   property System::String ^ Default;   // OK
};
```