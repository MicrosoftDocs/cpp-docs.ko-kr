---
description: '자세한 정보: 컴파일러 오류 C2774'
title: 컴파일러 오류 C2774
ms.date: 11/04/2016
f1_keywords:
- C2774
helpviewer_keywords:
- C2774
ms.assetid: 10f428c6-7f49-489a-92ba-6ef978b7caaf
ms.openlocfilehash: d934b2f85fe571c43c8db69018c7c13fd782226a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298203"
---
# <a name="compiler-error-c2774"></a>컴파일러 오류 C2774

' identifier ':이 속성과 연결 된 ' put ' 메서드가 없습니다.

[속성](../../cpp/property-cpp.md) 을 사용 하 여 선언 된 데이터 멤버에 `put` 함수가 없지만 식에서 해당 값을 설정 하려고 합니다.

다음 샘플에서는 C2774를 생성 합니다.

```cpp
// C2774.cpp
struct A {
   __declspec(property(get=GetProp)) int prop;
   int GetProp(void);

   __declspec(property(get=GetProp2, put=PutProp2)) int prop2;
   int GetProp2(void);
   void PutProp2(int);
};

int main() {
   A* pa = new A;
   int val = 0;
   pa->prop = val;   // C2774
   pa->prop++;   // C2774
}
```
