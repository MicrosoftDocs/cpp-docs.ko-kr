---
title: 컴파일러 오류 C2498
ms.date: 11/04/2016
f1_keywords:
- C2498
helpviewer_keywords:
- C2498
ms.assetid: 0839f12c-aaa4-4a02-bb33-7f072715dd14
ms.openlocfilehash: 1087dbb2297058f752e0a15776e4a7185e32a5c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360471"
---
# <a name="compiler-error-c2498"></a>컴파일러 오류 C2498

'function': 'novtable'는 클래스 선언 또는 정의에 적용 될 수 있습니다

이 오류를 사용 하 여 발생할 수 있습니다 `__declspec(novtable)` 함수를 사용 하 여 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2498 오류가 생성 됩니다.

```
// C2498.cpp
// compile with: /c
void __declspec(novtable) f() {}   // C2498
class __declspec(novtable) A {};   // OK
```