---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4683'
title: 컴파일러 경고(수준 1) C4683
ms.date: 08/27/2018
f1_keywords:
- C4683
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
ms.openlocfilehash: e7f2c76e7f15bb7342e60b2aa390cf0bd1a8ce05
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285242"
---
# <a name="compiler-warning-level-1-c4683"></a>컴파일러 경고(수준 1) C4683

> '*function*': 이벤트 소스에 ' out ' 매개 변수가 있습니다. 여러 이벤트 처리기를 후크 하는 경우 주의 해야 합니다.

## <a name="remarks"></a>설명

둘 이상의 이벤트 싱크가 COM 이벤트 소스를 수신 대기 하는 경우 out 매개 변수 값은 무시 될 수 있습니다.

메모리 누수는 다음과 같은 경우에 발생 합니다.

1. 메서드에 내부적으로 할당 되는 out 매개 변수가 있는 경우 (예: BSTR *)

2. 이벤트에 두 개 이상의 처리기가 있는 경우 (는 멀티 캐스트 이벤트)입니다.

누수가 발생 하는 이유는 out 매개 변수가 둘 이상의 처리기에 의해 설정 되 고 마지막 처리기에 의해서만 호출 사이트로 반환 되기 때문입니다.

## <a name="example"></a>예제

다음 샘플에서는 C4683를 생성 하 고 수정 하는 방법을 보여 줍니다.

```cpp
// C4683.cpp
// compile with: /W1 /LD
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[ module(name="xx") ];

[ object ]
__interface I {
   HRESULT f([out] int* pi);
   // try the following line instead
   // HRESULT f(int* pi);
};

[ coclass, event_source(com) ]
struct E {
   __event __interface I;   // C4683
};
```
