---
description: '자세히 알아보기: &lt; cstdarg&gt;'
title: '&lt;cstdarg&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdarg>
helpviewer_keywords:
- cstdarg header
ms.assetid: 639b4ef7-8408-4640-9343-41631f0ab663
ms.openlocfilehash: 4f009535cdcfec5d9e461aad4857335ddb86e1ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233255"
---
# <a name="ltcstdarggt"></a>&lt;cstdarg&gt;

C 표준 라이브러리 헤더를 포함 \<stdarg.h> 하 고 네임 스페이스에 연결 된 이름을 추가 합니다 `std` . 이 헤더를 포함 하면 C 표준 라이브러리 헤더의 외부 링크를 사용 하 여 선언한 이름이 네임 스페이스에 선언 됩니다 `std` .

## <a name="syntax"></a>Syntax

```cpp
#include <cstdarg>
```

## <a name="namespace-and-macros"></a>네임 스페이스 및 매크로

```cpp
namespace std {
    using va_list = see below;
}

#define va_arg(V, P)
#define va_copy(VDST, VSRC)
#define va_end(V)
#define va_start(V, P)
```

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
