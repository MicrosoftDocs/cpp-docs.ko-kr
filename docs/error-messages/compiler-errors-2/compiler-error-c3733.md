---
description: '자세한 정보: 컴파일러 오류 C3733'
title: 컴파일러 오류 C3733
ms.date: 11/04/2016
f1_keywords:
- C3733
helpviewer_keywords:
- C3733
ms.assetid: 0cc1a9fe-1400-4be3-b35a-16435cba7a5a
ms.openlocfilehash: 768586c760a06c502a08a8a11b8a1ad4e33c4e93
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245020"
---
# <a name="compiler-error-c3733"></a>컴파일러 오류 C3733

' event ': COM 이벤트를 지정 하기 위한 구문이 잘못 되었습니다. ' __interface '를 잊은 경우

COM 이벤트에 잘못 된 구문이 사용 되었습니다. 이 오류를 해결 하려면 이벤트 유형을 변경 하거나 구문을 수정 하 여 COM 이벤트 규칙을 준수 합니다.

다음 샘플에서는 C3733를 생성 합니다.

```
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[coclass, event_source(com), // change 'com' to 'native' to resolve
uuid("00000000-0000-0000-0000-000000000001")]
class A
{
   __event void func();   // C3733
};

int main()
{
}
```
