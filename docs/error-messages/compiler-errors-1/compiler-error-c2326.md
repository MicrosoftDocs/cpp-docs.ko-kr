---
description: '자세한 정보: 컴파일러 오류 C2326'
title: 컴파일러 오류 C2326
ms.date: 11/04/2016
f1_keywords:
- C2326
helpviewer_keywords:
- C2326
ms.assetid: 01a5ea40-de83-4e6f-a4e8-469f441258e0
ms.openlocfilehash: 968426bfc8752ebf1c33ed37a25923a3bd48bc29
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234958"
---
# <a name="compiler-error-c2326"></a>컴파일러 오류 C2326

'declarator': 함수에서 'name'에 액세스할 수 없습니다.

코드에서 멤버 변수를 수정하려고 하는데, 이는 불가능합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2326을 생성합니다.

```cpp
// C2326.cpp
void MyFunc() {
   int i;

   class MyClass  {
   public:
      void mf() {
         i = 4;   // C2326 i is inaccessible
      }
   };
}
```
