---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4526'
title: 컴파일러 경고(수준 1) C4526
ms.date: 11/04/2016
f1_keywords:
- C4526
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
ms.openlocfilehash: 13eddea0fcf82686333fe51d253c3b24552e18c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294823"
---
# <a name="compiler-warning-level-1-c4526"></a>컴파일러 경고(수준 1) C4526

' function ': 정적 멤버 함수는 가상 함수 ' 가상 함수를 재정의할 수 없습니다. 재정의는 무시 됩니다. 가상 함수는 숨겨집니다.

정적 멤버 함수는 가상 함수를 재정의 하는 조건을 충족 하 여 해당 멤버를 가상 및 정적 함수로 만듭니다.

다음 코드는 C4526을 생성 합니다.

```cpp
// C4526.cpp
// compile with: /W1 /c
// C4526 expected
struct myStruct1 {
   virtual void __stdcall func( int ) = 0;
};

struct myStruct2: public myStruct1 {
   static void __stdcall func( int );
};
```

가능한 수정 사항은 다음과 같습니다.

- 함수가 기본 클래스 가상 함수를 재정의 하기 위한 것 이라면 정적 지정자를 제거 합니다.

- 함수가 정적 멤버 함수가 될 경우 기본 클래스 가상 함수와 충돌 하지 않도록 이름을 바꿉니다.
