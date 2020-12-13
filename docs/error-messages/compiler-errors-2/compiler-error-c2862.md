---
description: '자세한 정보: 컴파일러 오류 C2862'
title: 컴파일러 오류 C2862
ms.date: 11/04/2016
f1_keywords:
- C2862
helpviewer_keywords:
- C2862
ms.assetid: c04d8499-b799-48a1-9fb4-7902a0b0ac8e
ms.openlocfilehash: 80b2a3d597c3289024d025bac35f5e0aeab44c58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151114"
---
# <a name="compiler-error-c2862"></a>컴파일러 오류 C2862

' interface ': 인터페이스에는 public 멤버만 사용할 수 있습니다.

Protected 및 private 멤버는 다른 멤버 함수 에서만 액세스할 수 있습니다. 이러한 멤버는 해당 멤버에 대 한 구현을 제공 하지 않을 수 있기 때문에 인터페이스에서 사용 되지 않습니다.

다음 샘플에서는 C2862를 생성 합니다.

```cpp
// C2862.cpp
// compile with: /c
#include <unknwn.h>

[object, uuid="60719E20-EF37-11D1-978D-0000F805D73B"]
__interface IMyInterface {
   HRESULT mf1(void);   // OK
protected:
   HRESULT mf2(int *b);   // C2862
private:
   HRESULT mf3(int *c);   // C2862
};
```
