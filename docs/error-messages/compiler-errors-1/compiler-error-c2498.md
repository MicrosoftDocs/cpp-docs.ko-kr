---
description: '자세한 정보: 컴파일러 오류 C2498'
title: 컴파일러 오류 C2498
ms.date: 11/04/2016
f1_keywords:
- C2498
helpviewer_keywords:
- C2498
ms.assetid: 0839f12c-aaa4-4a02-bb33-7f072715dd14
ms.openlocfilehash: e7cbb811cdaeea703d0f1da1c0f2012ebe8210fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335099"
---
# <a name="compiler-error-c2498"></a>컴파일러 오류 C2498

' function ': ' novtable '는 클래스 선언 또는 정의에만 적용할 수 있습니다.

이 오류는 함수와 함께를 사용 하 여 발생할 수 있습니다 `__declspec(novtable)` .

## <a name="example"></a>예제

다음 샘플에서는 C2498를 생성 합니다.

```cpp
// C2498.cpp
// compile with: /c
void __declspec(novtable) f() {}   // C2498
class __declspec(novtable) A {};   // OK
```
