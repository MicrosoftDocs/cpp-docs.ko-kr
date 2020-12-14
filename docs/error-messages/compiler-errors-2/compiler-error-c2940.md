---
description: '자세한 정보: 컴파일러 오류 C2940'
title: 컴파일러 오류 C2940
ms.date: 11/04/2016
f1_keywords:
- C2940
helpviewer_keywords:
- C2940
ms.assetid: af6bf2bf-8de6-4cfd-bbf0-4c6b32a30edf
ms.openlocfilehash: 2601e32d2e52d332e4f6443dde23b544d955aac1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249687"
---
# <a name="compiler-error-c2940"></a>컴파일러 오류 C2940

'class': type-class-id가 지역 typedef로 재정의됩니다.

제네릭 또는 템플릿 클래스를 로컬로 사용할 수 없습니다 **`typedef`** .

다음 샘플에서는 C2940을 생성합니다.

```cpp
// C2940.cpp
template<class T>
struct TC {};
int main() {
   typedef int TC<int>;   // C2940
   typedef int TC;   // OK
}
```

C2940은 제네릭을 사용하는 경우에도 발생할 수 있습니다.

```cpp
// C2940b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };

int main() {
   typedef int GC<int>;   // C2940
   typedef int GC;
}
```
