---
description: '자세한 정보: 컴파일러 오류 C3351'
title: 컴파일러 오류 C3351
ms.date: 11/04/2016
f1_keywords:
- C3351
helpviewer_keywords:
- C3351
ms.assetid: c021bbbe-1067-4f51-af4f-940d2b792eb5
ms.openlocfilehash: 324d927f0a54ea5750cbea45827152a66546cba7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144537"
---
# <a name="compiler-error-c3351"></a>컴파일러 오류 C3351

'object': 대리자 생성자: 두 번째 인수는 정적 멤버 함수 또는 전역 함수의 주소여야 합니다.

컴파일러에는 선언 된 함수의 주소가 필요 합니다 **`static`** .

다음 샘플에서는 C3351을 생성합니다.

```cpp
// C3351a.cpp
// compile with: /clr
delegate int D(int, int);

ref class C {
public:
   int mf(int, int) {
      return 1;
   }

   static int mf2(int, int) {
      return 1;
   }
};

int main() {
   System::Delegate ^pD = gcnew D(nullptr, &C::mf);   // C3351
   System::Delegate ^pD2 = gcnew D(&C::mf2);
}
```
