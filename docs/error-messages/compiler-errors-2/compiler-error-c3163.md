---
description: '자세한 정보: 컴파일러 오류 C3163'
title: 컴파일러 오류 C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: 53d0135e3083de7727b2a6c7f51a3f75e7314405
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203954"
---
# <a name="compiler-error-c3163"></a>컴파일러 오류 C3163

> '*구문*': 특성이 이전 선언과 일치 하지 않습니다.

정의에 적용 되는 특성이 선언에 적용 되는 특성과 충돌 합니다.

C3163를 해결 하는 한 가지 방법은 전방 선언에서 특성을 제거 하는 것입니다. 전방 선언에 대 한 모든 특성은 정의의 특성 또는 최대 값 보다 작아야 합니다.

C3163 오류의 가능한 원인은 Microsoft SAL (소스 코드 주석 언어)와 관련이 있습니다. 플래그를 사용 하 여 프로젝트를 컴파일하지 않으면 SAL 매크로가 확장 되지 않습니다 **`/analyze`** . 을 (를) 사용 하지 않고 컴파일하는 프로그램은 옵션을 사용 하 여 **`/analyze`** 다시 컴파일할 때 C3163을 throw 할 수 있습니다 **`/analyze`** . SAL에 대 한 자세한 내용은 [Sal 주석](../../c-runtime-library/sal-annotations.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3163를 생성 합니다.

```cpp
// C3163.cpp
// compile with: /clr /c
using namespace System;

[CLSCompliant(true)] void f();
[CLSCompliant(false)] void f() {}   // C3163
// try the following line instead
// [CLSCompliant(true)] void f() {}
```

## <a name="see-also"></a>참고 항목

[SAL 주석](../../c-runtime-library/sal-annotations.md)
