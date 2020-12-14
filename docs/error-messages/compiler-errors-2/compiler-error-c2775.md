---
description: '자세한 정보: 컴파일러 오류 C2775'
title: 컴파일러 오류 C2775
ms.date: 11/04/2016
f1_keywords:
- C2775
helpviewer_keywords:
- C2775
ms.assetid: 9c488508-ade0-48f1-b94f-d538d15f807a
ms.openlocfilehash: f7a24cfa3b868d08c86a08deaa13ec6067f4a9eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298164"
---
# <a name="compiler-error-c2775"></a>컴파일러 오류 C2775

' identifier ':이 속성과 연결 된 ' get ' 메서드가 없습니다.

확장 특성 [속성](../../cpp/property-cpp.md) 을 사용 하 여 선언 된 데이터 멤버에 `get` 함수를 지정 하지 않았지만 식이 해당 값을 검색 하려고 합니다.

다음 샘플에서는 C2775를 생성 합니다.

```cpp
// C2775.cpp
struct A {
   __declspec(property(put=PutProp2, get=GetProp2)) int prop2;
   int GetProp2(){return 0;}
   void PutProp2(int){}

   __declspec(property(put=PutProp)) int prop;
   int PutProp(void){}

};

int main() {
   A* pa = new A;
   int x;
   x = pa->prop;   // C2775
   x = pa->prop2;
}
```
