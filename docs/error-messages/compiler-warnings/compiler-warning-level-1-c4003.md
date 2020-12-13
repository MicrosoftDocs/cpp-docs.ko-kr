---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4003'
title: 컴파일러 경고 (수준 1) C4003
ms.date: 11/04/2016
f1_keywords:
- C4003
helpviewer_keywords:
- C4003
ms.assetid: 0ed1c285-4428-4c90-8131-86897e31f115
ms.openlocfilehash: d8a581e9cf6152a3e0e92832b36e5f61a94277f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335988"
---
# <a name="compiler-warning-level-1-c4003"></a>컴파일러 경고 (수준 1) C4003

'identifier' 매크로의 실제 매개 변수가 부족합니다.

매크로 정의의 정식 매개 변수 수가 매크로의 실제 매개 변수 개수를 초과 합니다. 매크로 확장은 누락 된 매개 변수에 대해 빈 텍스트를 대체 합니다.

다음 샘플에서는 C4003를 생성 합니다.

```cpp
// C4003.cpp
// compile with: /WX
#define test(a,b) (a+b)

int main()
{
   int a = 1;
   int b = 2;
   a = test(b);   // C4003
   // try..
   a = test(a,b);
}
```
