---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4540'
title: 컴파일러 경고(수준 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 8bd65d09abf48fc3653f160ebdf109235f3e1471
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212261"
---
# <a name="compiler-warning-level-1-c4540"></a>컴파일러 경고(수준 1) C4540

을 (를) 액세스할 수 없거나 모호한 기본으로 변환 하는 데 사용 dynamic_cast. 런타임 테스트가 실패 합니다 (' type1 '에서 ' type2 ' (으)로).

**`dynamic_cast`** 한 형식에서 다른 형식으로 변환 하는 데 사용 되었습니다. 컴파일러는 기본 클래스에 액세스할 수 없거나 (예의 경우) 모호한 경우 (예를 **`private`** 들어 클래스 계층 구조에 두 번 이상 표시 됨) 캐스팅이 항상 실패 (NULL 반환) 하는 것을 확인 했습니다.

다음은이 경고의 예를 보여 줍니다. 클래스 **B** 는 클래스 **A** 에서 파생 됩니다. 프로그램은 클래스 b **`dynamic_cast`** (파생 클래스  )에서 클래스 **A** 로 캐스팅 하는 데 사용 됩니다 .이는 클래스 **b** 가 이므로 액세스할 수 없기 때문에 항상 실패 **`private`** 합니다. 에 대 한 액세스 **를로 변경** 하면 **`public`** 경고가 해결 됩니다.

```cpp
// C4540.cpp
// compile with: /W1

struct A {
   virtual void g() {}
};

struct B : private A {
   virtual void g() {}
};

int main() {
   B b;
   A * ap = dynamic_cast<A*>(&b);   // C4540
}
```
