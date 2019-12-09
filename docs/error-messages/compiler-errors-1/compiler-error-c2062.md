---
title: 컴파일러 오류 C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: a709a540b24756a7e08f98552c5888a55c3ea601
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735972"
---
# <a name="compiler-error-c2062"></a>컴파일러 오류 C2062

예기치 않은 ' type ' 형식입니다.

컴파일러에서 형식 이름을 필요로 하지 않습니다.

다음 샘플에서는 C2062를 생성 합니다.

```cpp
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

C2062은 컴파일러가 생성자의 매개 변수 목록에서 정의 되지 않은 형식을 처리 하는 방식으로 인해 발생할 수도 있습니다. 컴파일러에서 정의 되지 않은 (철자가 틀린?) 형식이 발견 되 면 생성자가 식인 것으로 가정 하 고 C2062를 발생 시킵니다. 이 문제를 해결 하려면 생성자 매개 변수 목록에 정의 된 형식만 사용 합니다.
