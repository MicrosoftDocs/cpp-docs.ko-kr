---
description: '자세한 정보: 컴파일러 오류 C2156'
title: 컴파일러 오류 C2156
ms.date: 11/04/2016
f1_keywords:
- C2156
helpviewer_keywords:
- C2156
ms.assetid: 136f9c67-2c27-4f61-b7e6-ccd202eca697
ms.openlocfilehash: fa9954c52be278442d357dfa69071f83d10e49e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204136"
---
# <a name="compiler-error-c2156"></a>컴파일러 오류 C2156

pragma는 함수 외부에 있어야 합니다.

전역 수준(함수 본문 외부)에서 지정해야 하는 pragma가 함수 내에 있습니다.

다음 샘플에서는 C2156을 생성합니다.

```cpp
// C2156.cpp
#pragma optimize( "l", on )   // OK
int main() {
   #pragma optimize( "l", on )   // C2156
}
```
