---
description: '자세한 정보: 컴파일러 오류 C2757'
title: 컴파일러 오류 C2757
ms.date: 11/04/2016
f1_keywords:
- C2757
helpviewer_keywords:
- C2757
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
ms.openlocfilehash: e0be0f2a4c8dc5a5646400cbd0fa99e343ea82d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336182"
---
# <a name="compiler-error-c2757"></a>컴파일러 오류 C2757

' symbol ': 이름이 같은 기호가 이미 있으므로이 이름을 네임 스페이스 이름으로 사용할 수 없습니다.

현재 컴파일에서 네임 스페이스 식별자로 사용 되는 기호는 이미 참조 된 어셈블리에서 사용 되 고 있습니다.

다음 샘플에서는 C2757를 생성 합니다.

```cpp
// C2757a.cpp
// compile with: /clr /LD
public ref class Nes {};
```

그리고

```cpp
// C2757b.cpp
// compile with: /clr /c
#using <C2757a.dll>

namespace Nes {    // C2757
// try the following line instead
// namespace Nes2 {
   public ref class X {};
}
```
