---
description: '자세한 정보: 컴파일러 오류 C3898'
title: 컴파일러 오류 C3898
ms.date: 11/04/2016
f1_keywords:
- C3898
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
ms.openlocfilehash: 4b51683b13fa9328475ba09473ef1cae5663b009
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238962"
---
# <a name="compiler-error-c3898"></a>컴파일러 오류 C3898

' var ': 형식 데이터 멤버는 관리 되는 형식의 멤버일 수만 있습니다.

네이티브 클래스에서 [initonly](../../dotnet/initonly-cpp-cli.md) 데이터 멤버가 선언 되었습니다.  **`initonly`** 데이터 멤버는 CLR 클래스 에서만 선언할 수 있습니다.

다음 샘플에서는 C3898를 생성 합니다.

```cpp
// C3898.cpp
// compile with: /clr
struct Y1 {
   initonly
   static int data_var = 9;   // C3898
};
```

해결 방법:

```cpp
// C3898b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int data_var = 9;
};
```
