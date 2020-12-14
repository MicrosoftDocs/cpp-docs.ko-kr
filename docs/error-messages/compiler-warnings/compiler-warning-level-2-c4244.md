---
description: '자세한 정보: 컴파일러 경고 (수준 2) C4244'
title: 컴파일러 경고(수준 2) C4244
ms.date: 11/04/2016
f1_keywords:
- C4244
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
ms.openlocfilehash: b51af5179c9afbf01529f545bbc602ac9c9fac6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238130"
---
# <a name="compiler-warning-level-2-c4244"></a>컴파일러 경고(수준 2) C4244

' argument ': ' type1 '에서 ' type2 ' (으)로 변환 하 여 데이터가 손실 될 수 있습니다.

부동 소수점 형식이 정수 형식으로 변환 되었습니다.  데이터 손실이 발생했을 수 있습니다.

C4244 오류가 발생하는 경우 호환되는 형식을 사용하도록 프로그램을 변경하거나 코드에 일부 논리를 추가하여 가능한 값의 범위가 사용 중인 형식과 항상 호환되는지 확인해야 합니다.

C4244는 수준 3 및 4에서 실행할 수도 있습니다. 자세한 내용은 [컴파일러 경고 (수준 3 및 4) C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md) 를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4244 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C4244_level2.cpp
// compile with: /W2

int f(int x){ return 0; }
int main() {
   double x = 10.1;
   int i = 10;
   return (f(x));   // C4244
   // try the following line instead
   // return (f(i));
}
```
