---
description: '자세한 정보: 컴파일러 오류 C2833'
title: 컴파일러 오류 C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: 3c1bd2cc60478dc5868c74d4bfeac1d7d3a4d9a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194490"
---
# <a name="compiler-error-c2833"></a>컴파일러 오류 C2833

> ' operator *operator-name*'은 (는) 인식할 수 있는 연산자 또는 형식이 아닙니다.

단어 뒤에는 **`operator`** 재정의 하려는 *연산자 이름* 또는 변환 하려는 형식이 있어야 합니다.

관리 되는 형식에서 정의할 수 있는 연산자 목록은 [사용자 정의 연산자](../../dotnet/user-defined-operators-cpp-cli.md)를 참조 하세요.

다음 샘플에서는 C2833를 생성 합니다.

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
