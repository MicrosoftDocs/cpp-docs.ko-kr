---
description: '자세한 정보: 컴파일러 오류 C2178'
title: 컴파일러 오류 C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 7a93293fdb87f30827b8b9c3c6d38066b0c76798
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322164"
---
# <a name="compiler-error-c2178"></a>컴파일러 오류 C2178

'*identifier*'는 '*지정자*' 지정자를 사용 하 여 선언할 수 없습니다.

**`mutable`** 지정 자가 선언에서 사용 되었지만이 컨텍스트에서는 지정자를 사용할 수 없습니다.

**`mutable`** 지정자는 클래스 데이터 멤버의 이름에만 적용할 수 있으며 또는로 선언 된 이름에 적용할 수 **`const`** 없으며 **`static`** 참조 멤버에 적용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2178를 발생 시킬 수 있는 방법과이를 해결 하는 방법을 보여 줍니다.

```cpp
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
