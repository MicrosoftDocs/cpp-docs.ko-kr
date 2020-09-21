---
title: 컴파일러 오류 C2092
ms.date: 11/04/2016
f1_keywords:
- C2092
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
ms.openlocfilehash: 8f2b83b4099308ea1d0bb127d8cea377ab65da96
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741893"
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
