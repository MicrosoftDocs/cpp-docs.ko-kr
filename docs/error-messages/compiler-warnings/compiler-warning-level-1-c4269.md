---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4269'
title: 컴파일러 경고(수준 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 6b00eeee4a831ee7876556838f03d4b74f4790fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266132"
---
# <a name="compiler-warning-level-1-c4269"></a>컴파일러 경고(수준 1) C4269

' identifier ': 컴파일러에서 생성 된 기본 생성자로 초기화 된 ' const ' 자동 데이터는 불안정 한 결과를 생성 합니다.

**`const`** 특수 하지 않은 클래스의 자동 인스턴스는 컴파일러 생성 기본 생성자를 사용 하 여 초기화 됩니다.

## <a name="example"></a>예제

```cpp
// C4269.cpp
// compile with: /c /LD /W1
class X {
public:
   int m_data;
};

void g() {
   const X x1;   // C4269
};
```

클래스의이 인스턴스는 스택에서 생성 되기 때문에의 초기 값은 `m_data` 모두 일 수 있습니다. 또한 인스턴스 이기 때문에 **`const`** 의 값은 변경할 수 없습니다 `m_data` .
