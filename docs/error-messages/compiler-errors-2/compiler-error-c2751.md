---
description: '자세한 정보: 컴파일러 오류 C2751'
title: 컴파일러 오류 C2751
ms.date: 11/04/2016
f1_keywords:
- C2751
helpviewer_keywords:
- C2751
ms.assetid: 44a3abdf-8a87-4a09-b34b-532c220c310a
ms.openlocfilehash: 5eb41526946ee4318d8a1e96b04a527c828c914c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174457"
---
# <a name="compiler-error-c2751"></a>컴파일러 오류 C2751

' parameter ': 함수 매개 변수 이름을 한정할 수 없습니다.

정규화 된 이름을 함수 매개 변수로 사용할 수 없습니다.

다음 샘플에서는 C2751를 생성 합니다.

```cpp
// C2751.cpp
namespace std {
   template<typename T>
   class list {};
}

#define list std::list
void f(int &list){}   // C2751
```
