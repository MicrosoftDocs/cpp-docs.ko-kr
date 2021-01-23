---
description: '다음에 대 한 자세한 정보: 한 번 pragma'
title: 만 pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragma, once
no-loc:
- pragma
ms.openlocfilehash: 3edb5f88202ee783e587b1f886eddddf427f6133
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713482"
---
# <a name="once-no-locpragma"></a>`once` pragma

소스 코드 파일을 컴파일할 때 컴파일러에서 헤더 파일을 한 번만 포함 하도록 지정 합니다.

## <a name="syntax"></a>구문

> **`#pragma once`**

## <a name="remarks"></a>설명

를 사용 하면 `#pragma once` 컴파일러가 열리지 않고 `#include` 변환 단위에서 파일의 첫 번째 파일 다음에 다시 파일을 읽을 때 빌드 시간을 줄일 수 있습니다. *다중 포함 최적화* 라고 합니다. 이는 전처리기 매크로 정의를 사용 하 여 파일 내용이 여러 번 포함 되는 것을 방지 하는 *include 가드* 를 사용 하는 것과 비슷한 효과를 가집니다. 또한 *한 정의 규칙* 의 위반을 방지 하는 데 도움이 됩니다. 모든 템플릿, 형식, 함수 및 개체에 코드의 정의가 둘 이상 있어야 한다는 요구 사항이 있습니다.

예:

```cpp
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

`#pragma once` 지시문은 전처리기 기호를 사용하여 전역 네임스페이스가 잘못되는 것을 방지하기 때문에 새 코드에 사용하는 것이 좋습니다. 더 작은 입력이 필요 하며, 혼란을 줄이고 *기호 충돌* 을 일으킬 수 없습니다. 기호 충돌은 다른 헤더 파일이 가드 값과 동일한 전처리기 기호를 사용 하는 경우 발생 하는 오류입니다. C + + 표준에 포함 되지 않지만 몇 가지 일반적인 컴파일러를 통해 간단 구현 됩니다.

Include 가드를 같은 파일에 사용 하는 것은 장점이 없습니다 `#pragma once` . 컴파일러는 include 가드를 인식 하 고, `#pragma once` 설명의 표준 형식 앞 이나 뒤에 오는 주석이 없는 코드 또는 전처리기 지시문이 없는 경우 지시문과 동일한 방식으로 다중 포함 최적화를 구현 합니다.

```cpp
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

지시문을 구현 하지 않는 컴파일러에 코드를 이식 해야 하는 경우 `#pragma once` , 기존 코드와의 일관성을 유지 하기 위해 또는 다중 포함 최적화가 불가능 한 경우 가드를 포함 하는 것이 좋습니다. 이는 복잡 한 프로젝트에서 발생할 수 있습니다. 파일 시스템 별칭 지정 또는 별칭 포함 경로가 있으면 컴파일러가 정식 경로 별로 동일한 포함 파일을 식별 하지 못합니다.

`#pragma once`또는 전처리기 기호를 사용 하 여 효과를 제어 하는 여러 번 포함 되도록 디자인 된 헤더 파일의 include 가드를 사용 하지 않도록 주의 해야 합니다. 이 디자인의 예는 헤더 파일을 참조 \<assert.h> 하세요. 포함 된 파일에 대 한 여러 경로를 만들지 않도록 포함 경로를 관리 하는 것이 좋습니다 .이 경우 가드 및를 포함 하 여 여러 가지를 포함 하는 최적화가 모두 무효화 될 수 있습니다 `#pragma once` .

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
