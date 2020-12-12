---
description: '자세한 정보: 컴파일러 오류 C2447'
title: 컴파일러 오류 C2447
ms.date: 11/04/2016
f1_keywords:
- C2447
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
ms.openlocfilehash: c27846b002b3b58e3ed2e1dd89c06565b32d49b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189654"
---
# <a name="compiler-error-c2447"></a>컴파일러 오류 C2447

'{': 함수 헤더가 없습니다. 이전 스타일의 형식 목록입니까?

컴파일러가 전역 범위에서 예기치 않은 중괄호를 발견했습니다. 대부분의 경우 잘못된 형식의 함수 헤더, 위치가 잘못된 선언 또는 흩어진 세미콜론 때문입니다. 이 문제를 해결하려면 중괄호가 잘못된 형식의 함수 헤더 다음에 오고 선언 또는 흩어진 세미콜론이 앞에 오지 않는지 확인합니다.

이 오류는 이전 스타일의 C 언어 형식 인수 목록을 사용하는 경우에 발생할 수도 있습니다. 이 문제를 해결하려면 인수 목록을 리팩터링하여 현대적인 스타일을 사용하도록, 즉 괄호로 묶이도록 합니다.

다음 샘플에서는 C2447를 생성 합니다.

```cpp
// C2447.cpp
int c;
{}       // C2447
```
