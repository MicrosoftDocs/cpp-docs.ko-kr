---
description: '자세한 정보: 컴파일러 오류 C2433'
title: 컴파일러 오류 C2433
ms.date: 11/04/2016
f1_keywords:
- C2433
helpviewer_keywords:
- C2433
ms.assetid: 7079fedd-6059-4125-82ef-ebe275f1f9d1
ms.openlocfilehash: 67d7a0f34ef988c6d67a720a2af2d2fa493b2bf2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189953"
---
# <a name="compiler-error-c2433"></a>컴파일러 오류 C2433

' identifier ': ' modifier '는 데이터 선언에 사용할 수 없습니다.

**`friend`** **`virtual`** **`inline`** 데이터 선언에는, 및 한정자를 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2433를 생성 합니다.

```cpp
// C2433.cpp
class C{};

int main() {
   inline C c;   // C2433
}
```
