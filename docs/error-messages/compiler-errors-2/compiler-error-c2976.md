---
description: '자세한 정보: 컴파일러 오류 C2976'
title: 컴파일러 오류 C2976
ms.date: 11/04/2016
f1_keywords:
- C2976
helpviewer_keywords:
- C2976
ms.assetid: d9bf9836-325e-4f72-a7e3-a67cf19d32e7
ms.openlocfilehash: 645b4437bba022e53d018aec18d81b5f108d4d93
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281901"
---
# <a name="compiler-error-c2976"></a>컴파일러 오류 C2976

' identifier ': 형식 인수가 너무 적습니다.

제네릭 또는 템플릿에 실제 인수가 하나 이상 없습니다. 제네릭 또는 템플릿 선언을 확인하여 올바른 매개 변수 개수를 찾습니다.

이 오류는 c + + 표준 라이브러리 구성 요소에서 템플릿 인수가 누락 되었기 때문에 발생할 수 있습니다.

다음 샘플에서는 C2976를 생성 합니다.

```cpp
// C2976.cpp
template <class T>
struct TC {
   T t;
};
int main() {
   TC<>* t;   // C2976
   TC<int>* t2;   // OK
}
```

제네릭을 사용 하는 경우에도 C2976이 발생할 수 있습니다.

```cpp
// C2976b.cpp
// compile with: /clr
generic <class T>
ref struct GC {
   T t;
};

int main() {
   GC<>^ g;   // C2976
   GC<int>^ g2;   // OK
}
```
