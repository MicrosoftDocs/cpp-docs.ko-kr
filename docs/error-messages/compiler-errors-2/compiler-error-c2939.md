---
description: '자세한 정보: 컴파일러 오류 C 2939'
title: 컴파일러 오류 C2939
ms.date: 11/04/2016
f1_keywords:
- C2939
helpviewer_keywords:
- C2939
ms.assetid: 455b050b-f2dc-4b5b-bd6a-e1f81d3d1644
ms.openlocfilehash: 465d2d9535a1c8f393e21b4ef48707f8e5fab89b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323027"
---
# <a name="compiler-error-c2939"></a>컴파일러 오류 C2939

'class': type-class-id가 로컬 데이터 변수로 재정의되었습니다.

제네릭 또는 템플릿 클래스를 로컬 데이터 변수로 사용할 수 없습니다.

중괄호가 짝이 맞지 않는 경우 이 오류가 발생할 수 있습니다.

다음 샘플에서는 C2939를 생성합니다.

```cpp
// C2939.cpp
template<class T>
struct TC { };
int main() {
   int TC<int>;   // C2939
   int TC;   // OK
}
```

C2939는 제네릭을 사용하는 경우에도 발생할 수 있습니다.

```cpp
// C2939b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };

int main() {
   int GC<int>;   // C2939
   int GC;   // OK
}
```
