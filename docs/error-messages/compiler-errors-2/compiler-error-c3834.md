---
title: 컴파일러 오류 C3834
ms.date: 11/04/2016
f1_keywords:
- C3834
helpviewer_keywords:
- C3834
ms.assetid: 059e0dc4-300b-4e74-b6c2-41a57831fe2a
ms.openlocfilehash: 1dac75ca5bea868823eba8e344fb4ec043fae1ad
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741536"
---
# <a name="compiler-error-c3834"></a>컴파일러 오류 C3834

고정 포인터에 대 한 명시적 캐스트가 잘못 되었습니다. 대신 고정 된 지역 변수 사용

고정 된 포인터로 명시적으로 캐스팅 하는 것은 허용 되지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3834를 생성 합니다.

```cpp
// C3834.cpp
// compile with: /clr
int main() {
   int x = 33;

   pin_ptr<int> p = safe_cast<pin_ptr<int> >(&x);   // C3834
   pin_ptr<int> p2 = &x;   // OK
}
```
