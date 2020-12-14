---
description: '자세한 정보: 컴파일러 오류 C2533'
title: 컴파일러 오류 C2533
ms.date: 11/04/2016
f1_keywords:
- C2533
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
ms.openlocfilehash: 46f9a18d80bcf75d916a6cf5387dc7145f1f1629
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258124"
---
# <a name="compiler-error-c2533"></a>컴파일러 오류 C2533

'identifier': 생성자에서 반환 형식을 사용할 수 없습니다.

생성자는 반환 형식이 아니더라도 반환 형식을 가질 수 없습니다 **`void`** .

이 오류의 일반적인 출처는 클래스 정의의 끝과 첫 번째 생성자 구현 사이에 누락된 세미콜론입니다. 컴파일러는 생성자 함수에 대한 반환 형식의 정의로 클래스를 인식하고 C2533을 생성합니다.

다음 샘플에서는 C2533을 생성하고 해결 방법을 보여 줍니다.

```cpp
// C2533.cpp
// compile with: /c
class X {
public:
   X();
};

int X::X() {}   // C2533 - constructor return type not allowed
X::X() {}   // OK - fix by using no return type
```
