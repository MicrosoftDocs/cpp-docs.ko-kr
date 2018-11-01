---
title: lock::operator!=
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- lock.operator!=
- msclr.lock.operator!=
- msclr::lock::operator!=
- lock::operator!=
helpviewer_keywords:
- lock::operator!=
ms.assetid: ed1d674e-9ee9-4257-8a7e-2e3567d50222
ms.openlocfilehash: 5f202d6e7cc4c023b366f370ec2c419336822964
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558446"
---
# <a name="lockoperator"></a>lock::operator!=

같지 않음 연산자입니다.

## <a name="syntax"></a>구문

```
template<class T> bool operator!=(
   T t
);
```

#### <a name="parameters"></a>매개 변수

*t*<br/>
같지 않은지 비교할 개체입니다.

## <a name="return-value"></a>반환 값

반환 **true** 하는 경우 `t` 잠금의 개체에서 다른 **false** 그렇지 않은 경우.

## <a name="example"></a>예제

```cpp
// msl_lock_op_ineq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   Object^ o2 = gcnew Object;
   lock l1(o1);
   if (l1 != o2) {
      Console::WriteLine("Inequal!");
   }
}
```

```Output
Inequal!
```

## <a name="requirements"></a>요구 사항

**헤더 파일** \<msclr\lock.h >

**Namespace** msclr

## <a name="see-also"></a>참고 항목

[lock 멤버](../dotnet/lock-members.md)<br/>
[lock::operator==](../dotnet/lock-operator-equality.md)