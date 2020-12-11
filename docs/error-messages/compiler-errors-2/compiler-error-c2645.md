---
description: '자세한 정보: 컴파일러 오류 C2645'
title: 컴파일러 오류 C2645
ms.date: 11/04/2016
f1_keywords:
- C2645
helpviewer_keywords:
- C2645
ms.assetid: 6609c2fa-c3b2-4a6b-8e8d-58fb52f67175
ms.openlocfilehash: d757b171fd314a5ed90fafe76d1b45074ec5b604
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160833"
---
# <a name="compiler-error-c2645"></a>컴파일러 오류 C2645

멤버 포인터에 대 한 정규화 된 이름이 없습니다. ':: * '가 있습니다.

멤버에 대 한 포인터 선언이 클래스를 지정 하지 않습니다.

다음 샘플에서는 C2645를 생성 합니다.

```cpp
// C2645.cpp
class A {};
int main() {
   int B::* bp;   // C2645 B not defined
   int A::* ap;   // OK
}
```
