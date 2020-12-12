---
description: '자세한 정보: 컴파일러 오류 C2356'
title: 컴파일러 오류 C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: c0e2d179bb41e6cbae674d92976674ab90f05c0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328336"
---
# <a name="compiler-error-c2356"></a>컴파일러 오류 C2356

초기화 세그먼트는 변환 단위 동안 변경 되지 않아야 합니다.

가능한 원인:

- `#pragma init_seg` 세그먼트 초기화 코드 앞에

- `#pragma init_seg` 뒤에 다른 `#pragma init_seg`

이 문제를 해결 하려면 세그먼트 초기화 코드를 모듈의 시작 부분으로 이동 합니다. 여러 영역을 초기화 해야 하는 경우 별도의 모듈로 이동 합니다.

다음 샘플에서는 C2356를 생성 합니다.

```cpp
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```
