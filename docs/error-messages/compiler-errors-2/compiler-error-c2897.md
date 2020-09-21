---
title: 컴파일러 오류 C2897
ms.date: 11/04/2016
f1_keywords:
- C2897
helpviewer_keywords:
- C2897
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
ms.openlocfilehash: 22e63ce92a6d526f08e68bedb35de104be339dc3
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743375"
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
