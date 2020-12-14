---
description: '자세한 정보: 컴파일러 오류 C3883'
title: 컴파일러 오류 C3883
ms.date: 11/04/2016
f1_keywords:
- C3883
helpviewer_keywords:
- C3883
ms.assetid: cdd1c1f4-f268-4469-9c62-d52303114b0c
ms.openlocfilehash: 216cfdc6385f12ff565eca581068ac5625a09044
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274426"
---
# <a name="compiler-error-c3883"></a>컴파일러 오류 C3883

' var ': initonly 정적 데이터 멤버를 초기화 해야 합니다.

[Initonly](../../dotnet/initonly-cpp-cli.md) 로 표시 된 변수가 올바르게 초기화 되지 않았습니다.

다음 샘플에서는 C3883를 생성 합니다.

```cpp
// C3883.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   static int staticConst1;   // C3883
};
```

다음 샘플에는 가능한 해결 방법을 보여 줍니다.

```cpp
// C3883b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst2 = 0;
};
```

다음 샘플에서는 정적 생성자에서를 초기화 하는 방법을 보여 줍니다.

```cpp
// C3883c.cpp
// compile with: /clr /LD
ref struct Y1 {
   initonly
   static int staticConst1;

   static Y1() {
      staticConst1 = 0;
   }
};
```
