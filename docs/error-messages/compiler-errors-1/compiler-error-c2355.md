---
description: '자세한 정보: 컴파일러 오류 C2355'
title: 컴파일러 오류 C2355
ms.date: 11/04/2016
f1_keywords:
- C2355
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
ms.openlocfilehash: f28799d4fbd72c7a5959bc4c68e1810b26052844
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328377"
---
# <a name="compiler-error-c2355"></a>컴파일러 오류 C2355

'this': 비정적 멤버 함수 또는 비정적 데이터 멤버 이니셜라이저 안에서만 참조할 수 있습니다.

포인터는 비정적 **`this`** 멤버 함수 또는 비정적 데이터 멤버 이니셜라이저 내 에서만 사용할 수 있습니다. 이 오류는 클래스 선언 외부에서 멤버 함수 정의의 클래스 범위가 제대로 정규화되지 않은 경우 발생할 수 있습니다. **`this`** 클래스에 선언 되지 않은 함수에서 포인터가 사용 되는 경우에도 오류가 발생할 수 있습니다.

이 문제를 해결하려면 멤버 함수 정의가 클래스의 멤버 함수 선언과 일치하는지, 정적으로 선언되지 않았는지 확인합니다. 데이터 멤버 이니셜라이저의 경우 데이터 멤버가 정적으로 선언되지 않았는지 확인합니다.

다음 샘플에서는 C2355를 생성하고 해결 방법을 보여 줍니다.

```cpp
// C2355.cpp
// compile with: /c
class MyClass {};
MyClass *p = this;   // C2355

// OK
class MyClass2 {
public:
   void Test() {
      MyClass2 *p = this;
   }
};
```
