---
description: '자세한 정보: 컴파일러 오류 C2423'
title: 컴파일러 오류 C2423
ms.date: 11/04/2016
f1_keywords:
- C2423
helpviewer_keywords:
- C2423
ms.assetid: 8797fb8b-b58b-4add-b6e6-2a9a3cd9084d
ms.openlocfilehash: 902a02d4bad34b3a386b95a72c8eca59dac19156
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120232"
---
# <a name="compiler-error-c2423"></a>컴파일러 오류 C2423

' number ': 소수 자릿수가 잘못 되었습니다.

인라인 어셈블리 코드는 1, 2, 4 또는 8이 아닌 숫자를 사용 하 여 레지스터의 크기를 조정 합니다.

다음 샘플에서는 C2423를 생성 합니다.

```cpp
// C2423.cpp
// processor: x86
int main() {
   _asm {
      lea EAX, [EAX*3]   // C2423
      lea EAX, [EAX+EAX*2]   // OK
   }
}
```
