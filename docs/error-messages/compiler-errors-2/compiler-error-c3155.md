---
description: '자세한 정보: 컴파일러 오류 C3155'
title: 컴파일러 오류 C3155
ms.date: 11/04/2016
f1_keywords:
- C3155
helpviewer_keywords:
- C3155
ms.assetid: b04a42e1-64e7-40f8-81fe-c7945348b2cf
ms.openlocfilehash: 92fdf24c067c26502f8d24923e7f2c77b16c7922
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242459"
---
# <a name="compiler-error-c3155"></a>컴파일러 오류 C3155

속성 인덱서에는 특성을 사용할 수 없습니다.

인덱싱된 속성이 잘못 선언 되었습니다. 자세한 내용은 [방법: c + +/cli에서 속성 사용](../../dotnet/how-to-use-properties-in-cpp-cli.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3155를 생성 합니다.

```cpp
// C3155.cpp
// compile with: /clr /c
using namespace System;
ref struct R {
   property int F[[ParamArray] int] {   // C3155
   // try the following line instead
   // property int F[ int] {   // OK
      int get(int i) {
         return 0;
      }
   }
};
```
