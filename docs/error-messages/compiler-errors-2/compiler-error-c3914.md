---
description: '자세한 정보: 컴파일러 오류 C3914'
title: 컴파일러 오류 C3914
ms.date: 11/04/2016
f1_keywords:
- C3914
helpviewer_keywords:
- C3914
ms.assetid: 8f3190e6-ee50-4916-9ecc-3b8748b2e1e7
ms.openlocfilehash: 7f5291e09d7f3f794d7d1bec90f0a753d7dfe38f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143964"
---
# <a name="compiler-error-c3914"></a>컴파일러 오류 C3914

기본 속성은 정적일 수 없습니다.

기본 속성이 잘못 선언 되었습니다.  자세한 내용은 [방법: c + +/cli에서 속성 사용](../../dotnet/how-to-use-properties-in-cpp-cli.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3914를 생성 하 고 수정 하는 방법을 보여 줍니다.

```cpp
// C3914.cpp
// compile with: /clr /c
ref struct X {
   static property int default[int] {   // C3914
   // try the following line instead
   // property int default[int] {
      int get(int) { return 0; }
      void set(int, int) {}
   }
};
```
