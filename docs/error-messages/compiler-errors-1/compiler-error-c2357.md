---
description: '자세한 정보: 컴파일러 오류 C2357'
title: 컴파일러 오류 C2357
ms.date: 11/04/2016
f1_keywords:
- C2357
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
ms.openlocfilehash: a58317fc4706d6385d3753a434c8e4fd80dc79b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276740"
---
# <a name="compiler-error-c2357"></a>컴파일러 오류 C2357

' identifier ': ' type ' 형식의 함수 여야 합니다.

코드에서 `atexit` 컴파일러가 내부적으로 선언 된 버전과 일치 하지 않는 함수의 버전을 선언 합니다. 다음과 `atexit` 같이 선언 합니다.

```
int __cdecl atexit(void (__cdecl *)());
```

자세한 내용은 [init_seg](../../preprocessor/init-seg.md)를 참조 하세요.

다음 샘플에서는 C2357를 생성 합니다.

```cpp
// C2357.cpp
// compile with: /c
// C2357 expected
#pragma warning(disable : 4075)
// Uncomment the following line to resolve.
// int __cdecl myexit(void (__cdecl *)());
#pragma init_seg(".mine$m",myexit)
```
