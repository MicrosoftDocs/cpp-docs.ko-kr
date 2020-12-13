---
description: '자세한 정보: 컴파일러 오류 C3309'
title: 컴파일러 오류 C3309
ms.date: 11/04/2016
f1_keywords:
- C3309
helpviewer_keywords:
- C3309
ms.assetid: 75ee16e3-7d4e-4c41-b3cb-64e9849c3aab
ms.openlocfilehash: e18f306b58cf4c5480d32305f6dcc8c9070a8768
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337381"
---
# <a name="compiler-error-c3309"></a>컴파일러 오류 C3309

'macro_name': 모듈 이름은 매크로 또는 키워드일 수 없습니다.

모듈 특성의 name 속성에 전달하는 값은 확장할 전처리기의 기호일 수 없습니다. 문자열 리터럴이어야 합니다.

다음 샘플에서는 C3309를 생성합니다.

```cpp
// C3309.cpp
#define NAME MyModule
[module(name="NAME")];   // C3309
// Try the following line instead
// [module(name="MyModule")];
[coclass]
class MyClass {
public:
   void MyFunc();
};

int main() {
}
```
