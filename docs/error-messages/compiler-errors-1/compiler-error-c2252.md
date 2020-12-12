---
description: '자세한 정보: 컴파일러 오류 C2252'
title: 컴파일러 오류 C2252
ms.date: 11/04/2016
f1_keywords:
- C2252
helpviewer_keywords:
- C2252
ms.assetid: fee74ab9-1997-4615-82fe-e6d1fe3aacd9
ms.openlocfilehash: 491ec4c600ab480322917d50822ede01a08dcfb5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134825"
---
# <a name="compiler-error-c2252"></a>컴파일러 오류 C2252

현재 범위에서 템플릿을 명시적으로 인스턴스화할 수 없습니다.

컴파일러가 템플릿의 명시적 인스턴스화와 관련 된 문제를 발견 했습니다.  예를 들어 함수에서 템플릿을 명시적으로 인스턴스화할 수 없습니다.

다음 샘플에서는 C2252를 생성 합니다.

```cpp
// C2252.cpp
class A {
public:
   template <class T>
   int getit(int i , T * it ) {
      return i;
   }
   template int A::getit<double>(int i, double * it);   // C2252
   // try the following line instead
   // template <> int A::getit<double>(int i, double * it);

};

int main() {
   // cannot explicitly instantiate in function
   template int A::getit<long>(int i, long * it);   // C2252
}
```
