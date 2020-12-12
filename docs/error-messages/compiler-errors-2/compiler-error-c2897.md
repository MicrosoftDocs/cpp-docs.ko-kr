---
description: '자세한 정보: 컴파일러 오류 C2897'
title: 컴파일러 오류 C2897
ms.date: 11/04/2016
f1_keywords:
- C2897
helpviewer_keywords:
- C2897
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
ms.openlocfilehash: b1a1f66987aa4bbd01fdf12f88f8933e3436938a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270877"
---
# <a name="compiler-error-c2897"></a>컴파일러 오류 C2897

소멸자/종료자는 함수 템플릿이 될 수 없습니다.

소멸자 또는 종료자는 오버 로드 될 수 없으므로 소멸자를 템플릿으로 선언 하는 것은 허용 되지 않습니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2897를 생성 합니다.

```cpp
// C2897.cpp
// compile with: /c
class X {
public:
   template<typename T> ~X() {}   // C2897
};
```

다음 샘플에서는 C2897를 생성 합니다.

```cpp
// C2897_b.cpp
// compile with: /c /clr
ref struct R2 {
protected:
   template<typename T> !R2(){}   // C2897 error
};
```
