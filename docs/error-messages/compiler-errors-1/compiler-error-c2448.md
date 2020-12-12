---
description: '자세한 정보: 컴파일러 오류 C2448'
title: 컴파일러 오류 C2448
ms.date: 11/04/2016
f1_keywords:
- C2448
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
ms.openlocfilehash: 8dc6f794a71c89b4b14d0a3f33d5617e296b3dc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189615"
---
# <a name="compiler-error-c2448"></a>컴파일러 오류 C2448

' identifier ': 함수 스타일 이니셜라이저가 함수 정의로 표시 됩니다.

함수 정의가 잘못 되었습니다.

이 오류는 이전 스타일의 C 언어 형식 목록으로 인해 발생할 수 있습니다.

다음 샘플에서는 C2448를 생성 합니다.

```cpp
// C2448.cpp
void func(c)
   int c;
{}   // C2448
```
