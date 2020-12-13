---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4312'
title: 컴파일러 경고(수준 1) C4312
ms.date: 11/04/2016
f1_keywords:
- C4312
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
ms.openlocfilehash: 52e165fd30a9171c1a08aa16f78cc1f298271b17
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340075"
---
# <a name="compiler-warning-level-1-c4312"></a>컴파일러 경고(수준 1) C4312

'identifier' : 'type1'에서 더 큰 'type2'(으)로의 변환입니다.

이 경고는 64 비트 포인터 형식 (예: 32 비트 **`int`** 또는 64 비트 포인터로 캐스팅)에 32 비트 값을 할당 하려는 시도를 검색 **`long`** 합니다.

이 변환은 부호 확장이 발생할 경우 32비트에 맞는 포인터 값에서도 안전하지 않을 수 있습니다. 음의 32비트 정수가 64비트 포인터 형식에 할당될 경우 부호 확장으로 인해 포인터 값이 정수의 값과 다른 메모리 주소를 참조할 수 있습니다.

이 경고는 64비트 컴파일 대상에 대해서만 표시됩니다. 자세한 내용은 [포인터 사용에 대 한 규칙](/windows/win32/WinProg64/rules-for-using-pointers)을 참조 하세요.

다음 코드 예제에서는 64비트 대상에 대해 컴파일되는 경우의 C4312를 생성합니다.

```cpp
// C4312.cpp
// compile by using: cl /W1 /LD C4312.cpp
void* f(int i) {
   return (void*)i;   // C4312 for 64-bit targets
}

void* f2(__int64 i) {
   return (void*)i;   // OK
}
```
