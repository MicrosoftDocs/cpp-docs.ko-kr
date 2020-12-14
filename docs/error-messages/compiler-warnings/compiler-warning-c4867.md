---
description: '자세한 정보: 컴파일러 경고 C4867'
title: 컴파일러 경고 C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: d9d263c041e12ff985ec5e46eb56a0af99bcf69d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315025"
---
# <a name="compiler-warning-c4867"></a>컴파일러 경고 C4867

' function ': 함수 호출에 인수 목록이 없습니다. ' call '을 사용 하 여 멤버에 대 한 포인터 만들기

멤버 함수에 대 한 포인터가 잘못 초기화 되었습니다.

이 경고는 Visual Studio 2005에 대해 수행 된 컴파일러 규칙 작업의 결과로 생성 될 수 있습니다. 향상 된 멤버 포인터 규칙입니다.  Visual Studio 2005 이전에 컴파일된 코드는 이제 C4867을 생성 합니다.

이 경고는 항상 오류로 실행 됩니다. [warning](../../preprocessor/warning.md) pragma를 사용하여 이 경고를 사용하지 않도록 설정합니다. C4867 및 MFC/ATL에 대 한 자세한 내용은 [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4867를 생성 합니다.

```cpp
// C4867.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b = {f};   // C4867
      B b2 = {&A::f};   // OK
   }
};
```
