---
description: '자세한 정보: 컴파일러 오류 C2381'
title: 컴파일러 오류 C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: ccaed8e5fc637ffb7e5cd2a33a00ddb5cf7c102b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282181"
---
# <a name="compiler-error-c2381"></a>컴파일러 오류 C2381

' function ': 재정의 __declspec (noreturn)이 다릅니다.

함수를 선언 하 고 정의 했지만 정의가 [noreturn](../../cpp/noreturn.md) 한정자를 사용 했습니다 **`__declspec`** . 는 `noreturn` 함수 재정의를 구성 합니다. 선언 및 정의는를 사용 하는 데 동의 해야 합니다 `noreturn` .

다음 샘플에서는 C2381를 생성 합니다.

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```
