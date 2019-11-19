---
title: 컴파일러 경고 (수준 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 8e514f4f3cf0cc3ee95ff709eda307b143ab3b1c
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965694"
---
# <a name="compiler-warning-level-1-c4540"></a>컴파일러 경고 (수준 1) C4540

을 (를) 액세스할 수 없거나 모호한 기본으로 변환 하는 데 사용 dynamic_cast. 런타임 테스트가 실패 합니다 (' type1 '에서 ' type2 ' (으)로).

`dynamic_cast`를 사용 하 여 한 형식에서 다른 형식으로 변환 했습니다. 컴파일러는 기본 클래스에 액세스할`private`수 없거나 (예를 들어), 모호한 경우 (예를 들어 클래스 계층 구조에 두 번 이상 표시 됨) 캐스팅이 항상 실패 ( **NULL**반환) 한다고 결정 했습니다.

다음은이 경고의 예를 보여 줍니다. 클래스 **B** 는 클래스 **A**에서 파생 됩니다. 이 프로그램은 `dynamic_cast`를 사용 하 여 클래스 **b** (파생 클래스)에서 클래스 **A**로 캐스팅 합니다. 클래스 **b** 는 `private` 되어 액세스할 수 없기 때문에 항상 실패 합니다. 에 **대 한 액세스** 를 **public** 으로 변경 하면 경고가 해결 됩니다.

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