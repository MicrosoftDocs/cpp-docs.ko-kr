---
description: '자세한 정보: 컴파일러 오류 C3457'
title: 컴파일러 오류 C3457
ms.date: 11/04/2016
f1_keywords:
- C3457
helpviewer_keywords:
- C3457
ms.assetid: 5c1e366a-fa75-4cca-b9a3-86d4ebe4090e
ms.openlocfilehash: 42e30946c57da585ed1339e49b6081372b141a2c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113599"
---
# <a name="compiler-error-c3457"></a>컴파일러 오류 C3457

'attribute': 특성은 명명되지 않은 인수를 지원하지 않습니다.

CLR 사용자 지정 특성 또는 컴파일러 특성과 달리 소스 주석 특성은 명명된 인수만 지원합니다.

## <a name="example"></a>예제

다음 샘플에서는 C3457을 생성합니다.

```
#include "SourceAnnotations.h"
[vc_attributes::Post( 1 )] int f();   // C3457
[vc_attributes::Post( Valid=vc_attributes::Yes )] int f2();   // OK
```
