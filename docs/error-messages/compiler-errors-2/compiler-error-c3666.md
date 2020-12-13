---
description: '자세한 정보: 컴파일러 오류 C3666'
title: 컴파일러 오류 C3666
ms.date: 11/04/2016
f1_keywords:
- C3666
helpviewer_keywords:
- C3666
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
ms.openlocfilehash: 245fd061a7a1ce7b9b3e25ae76e6b15ec9428145
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134266"
---
# <a name="compiler-error-c3666"></a>컴파일러 오류 C3666

' constructor ': 재정의 지정자 ' keyword '는 생성자에서 사용할 수 없습니다.

재정의 지정 자가 생성자에서 사용 되었으며이는 허용 되지 않습니다. 자세한 내용은 [Override 지정자](../../extensions/override-specifiers-cpp-component-extensions.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3666를 생성 합니다.

```cpp
// C3666.cpp
// compile with: /clr /c
ref struct R {
   R() new {}   // C3666
   R(int i) {}   // OK
};
```
