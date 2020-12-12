---
description: '자세한 정보: 컴파일러 오류 C2937'
title: 컴파일러 오류 C2937
ms.date: 11/04/2016
f1_keywords:
- C2937
helpviewer_keywords:
- C2937
ms.assetid: 95671ca3-79f7-4b56-a5f2-a92296da1629
ms.openlocfilehash: af73e4564293fdcd5b69cc2f1890cb3e5364c618
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323053"
---
# <a name="compiler-error-c2937"></a>컴파일러 오류 C2937

'class': type-class-id가 전역 typedef로 재정의되었습니다.

제네릭 또는 템플릿 클래스를 전역으로 사용할 수 없습니다 **`typedef`** .

다음 샘플에서는 C2937을 생성합니다.

```cpp
// C2937.cpp
// compile with: /c
template<class T>
struct TC { };
typedef int TC<int>;   // C2937
typedef TC<int> c;   // OK
```

C2937은 제네릭을 사용하는 경우에도 발생할 수 있습니다.

```cpp
// C2937b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };
typedef int GC<int>;   // C2937
typedef GC<int> xx;   // OK
```
