---
description: '자세히 알아보기: &lt; cassert&gt;'
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: e2b515fe492e6847c4d0cc5841dc43a2d879dd99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325358"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

C 표준 라이브러리 헤더를 포함 \<assert.h> 하 고 네임 스페이스에 연결 된 이름을 추가 합니다 `std` . 이 헤더를 포함 하면 C 표준 라이브러리 헤더의 외부 링크를 사용 하 여 선언한 이름이 네임 스페이스에 선언 됩니다 `std` .

> [!NOTE]
> \<assert.h> 매크로를 정의 하지 않습니다 **`static_assert`** .

## <a name="syntax"></a>Syntax

```cpp
#include <cassert>
```

## <a name="macros"></a>Macros

```cpp
#define assert(E)
```

### <a name="remarks"></a>설명

`assert(E)` 는 상수입니다. NDEBUG가 `assert` 마지막으로 정의 되거나 재정의 된 위치에 정의 되어 있거나 부울로 변환 된 *E* 가로 계산 되는 경우에만입니다 **`true`** .

## <a name="see-also"></a>참고 항목

[assert 매크로, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
