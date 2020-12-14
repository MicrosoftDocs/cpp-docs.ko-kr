---
description: '자세한 정보: 컴파일러 오류 C2530'
title: 컴파일러 오류 C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 07980fb6d87b4e84bc0b253ccd317eba02fa81af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258111"
---
# <a name="compiler-error-c2530"></a>컴파일러 오류 C2530

' identifier ': 참조를 초기화 해야 합니다.

이미 선언 되지 않은 경우 참조를 선언할 때 초기화 해야 합니다.

- [Extern](../../cpp/extern-cpp.md)키워드를 사용 합니다.

- 클래스, 구조체 또는 공용 구조체의 멤버 (및 생성자에서 초기화 됨)

- 함수 선언 또는 정의의 매개 변수로

- 함수의 반환 형식으로 반환 됩니다.

다음 샘플에서는 C2530를 생성 합니다.

```cpp
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```
