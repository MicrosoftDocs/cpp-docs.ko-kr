---
description: '자세한 정보: 컴파일러 오류 C2701'
title: 컴파일러 오류 C2701
ms.date: 11/04/2016
f1_keywords:
- C2701
helpviewer_keywords:
- C2701
ms.assetid: 31cf2ab7-ced9-4f75-aa51-e169e20407fb
ms.openlocfilehash: c82bc2f62811b8f16af4ccfaad9648efe4ee6c16
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144848"
---
# <a name="compiler-error-c2701"></a>컴파일러 오류 C2701

' function ': 함수 템플릿은 지역 클래스의 friend가 될 수 없습니다.

지역 클래스에는 friend 함수로 템플릿 함수를 사용할 수 없습니다.

다음 샘플에서는 C2701를 생성 합니다.

```cpp
// C2701.cpp
// compile with: /c
template<typename T>   // OK
void f1(const T &);

void MyFunction() {
   class MyClass {
      template<typename T> friend void f2(const T &);   // C2701
   };
}
```
