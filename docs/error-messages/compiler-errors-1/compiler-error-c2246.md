---
description: '자세한 정보: 컴파일러 오류 C2246'
title: 컴파일러 오류 C2246
ms.date: 11/04/2016
f1_keywords:
- C2246
helpviewer_keywords:
- C2246
ms.assetid: 4f3e4f83-21f3-4256-af96-43e0bb060311
ms.openlocfilehash: 1868389c98dd864e7d92bf33d57dbe96b831f3e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302206"
---
# <a name="compiler-error-c2246"></a>컴파일러 오류 C2246

'identifier': 지역으로 정의된 클래스에 잘못된 정적 데이터 멤버가 있습니다.

로컬 범위를 가진 클래스, 구조체 또는 공용 구조체의 멤버가 선언 됩니다 **`static`** .

다음 샘플에서는 C2246을 생성합니다.

```cpp
// C2246.cpp
// compile with: /c
void func( void ) {
   class A { static int i; };   // C2246  i is local to func
   static int j;   // OK
};
```
