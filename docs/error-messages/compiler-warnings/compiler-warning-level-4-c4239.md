---
title: 컴파일러 경고(수준 4) C4239
ms.date: 11/04/2016
f1_keywords:
- C4239
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
ms.openlocfilehash: 25b97cfb50847a0929f3d3a97b822209e6a11900
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686680"
---
# <a name="compiler-warning-level-4-c4239"></a>컴파일러 경고(수준 4) C4239

비표준 확장이 사용 됨: ' token ': ' type '에서 ' type ' (으)로 변환 합니다.

이 형식 변환은 c + + 표준에서 허용 되지 않지만 여기서는 확장으로 허용 됩니다. 이 경고는 항상 위반 되는 언어 규칙을 설명 하는 하나 이상의 설명 줄이 나옵니다.

## <a name="examples"></a>예제

다음 샘플에서는 C 4239를 생성 합니다.

```cpp
// C4239.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

void func(void) {
   C & rC = C();   // C4239
   const C & rC2 = C();   // OK
   rC2;
}
```

정수 계열 형식에서 열거형 형식으로의 변환은 허용 되지 않습니다.

다음 샘플에서는 C 4239를 생성 합니다.

```cpp
// C4239b.cpp
// compile with: /W4 /c
enum E { value };
struct S {
   E e : 2;
} s = { 5 };   // C4239
// try the following line instead
// } s = { (E)5 };
```
