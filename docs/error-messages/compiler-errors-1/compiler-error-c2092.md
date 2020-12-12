---
description: '자세한 정보: 컴파일러 오류 C2092'
title: 컴파일러 오류 C2092
ms.date: 11/04/2016
f1_keywords:
- C2092
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
ms.openlocfilehash: 3f89d735d44b3cc0b2c28013ab957bf433159afb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251884"
---
# <a name="compiler-error-c2092"></a>컴파일러 오류 C2092

' array name ' 배열 요소 형식은 함수 일 수 없습니다.

함수 배열을 사용할 수 없습니다. 함수에 대 한 포인터 배열을 사용 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2092를 생성 합니다.

```cpp
// C2092.cpp
typedef void (F) ();
typedef F AT[10];   // C2092
```

해결 방법:

```cpp
// C2092b.cpp
// compile with: /c
typedef void (F) ();
typedef F * AT[10];
```
