---
description: '자세한 정보: 컴파일러 오류 C2130'
title: 컴파일러 오류 C2130
ms.date: 11/04/2016
f1_keywords:
- C2130
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
ms.openlocfilehash: 78e7b756d5902562c6093e3f26f9934e87e732ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323183"
---
# <a name="compiler-error-c2130"></a>컴파일러 오류 C2130

\#줄에 파일 이름을 포함 하는 문자열이 있어야 하는데 ' token '이 있습니다.

[#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` 뒤에 오는 선택적 파일 이름 토큰은 문자열이어야 합니다.

다음 샘플에서는 C2130을 생성합니다.

```cpp
// C2130.cpp
int main() {
   #line 1000 test   // C2130
   #line 1000 "test"   // OK
}
```
