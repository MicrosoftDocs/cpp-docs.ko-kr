---
title: 컴파일러 오류 C3218
ms.date: 11/04/2016
f1_keywords:
- C3218
helpviewer_keywords:
- C3218
ms.assetid: 0eea19e0-503e-4e07-ae8b-2cb2e95922cd
ms.openlocfilehash: 386a0c180dd01161ebccdd2b04e899e0cc999614
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737987"
---
# <a name="compiler-error-c3218"></a>컴파일러 오류 C3218

' type ': 형식은 제약 조건으로 사용할 수 없습니다.

형식이 제약 조건 이어야 하는 경우에는 값 형식 이거나 관리 되는 클래스 또는 인터페이스에 대 한 참조 여야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C3218를 생성 합니다.

```cpp
// C3218.cpp
// compile with: /clr /c
class A {};
ref class B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C3218
ref class C {};

// OK
generic <class T>
where  T : B
ref class D {};
```
