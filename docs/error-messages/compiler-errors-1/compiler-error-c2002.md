---
description: '자세한 정보: 컴파일러 오류 C2002'
title: 컴파일러 오류 C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: acf6e0679f2579d25d37ccf0c11965bc1d8b436a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298619"
---
# <a name="compiler-error-c2002"></a>컴파일러 오류 C2002

와이드 문자 상수가 잘못 되었습니다.

멀티 바이트 문자 상수가 잘못 되었습니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 와이드 문자 상수에 예상 보다 많은 바이트가 포함 되어 있습니다.

1. 표준 헤더 STDDEF. h는 포함 되지 않습니다.

1. 와이드 문자는 일반 문자열 리터럴과 연결 될 수 없습니다.

1. 와이드 문자 상수는 ' L ' 문자 뒤에와 야 합니다.

    ```
    L'mbconst'
    ```

1. Microsoft c + +의 경우 전처리기 지시문의 텍스트 인수는 ASCII 여야 합니다. 예를 들어, 지시문은 `#pragma message(L"string")` 유효 하지 않습니다.
