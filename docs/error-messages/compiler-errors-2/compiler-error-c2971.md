---
description: '자세한 정보: 컴파일러 오류 C2971'
title: 컴파일러 오류 C2971
ms.date: 11/04/2016
f1_keywords:
- C2971
helpviewer_keywords:
- C2971
ms.assetid: fdb5467b-9a41-41ef-ac20-2e9428d5a4fc
ms.openlocfilehash: 51cecf7fcf80b93231763bb183b870760820ca7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210389"
---
# <a name="compiler-error-c2971"></a>컴파일러 오류 C2971

' class ': 템플릿 매개 변수 ' param ': ' arg ': 지역 변수를 비 형식 인수로 사용할 수 없습니다.

지역 변수의 이름 또는 주소를 템플릿 인수로 사용할 수 없습니다.

다음 샘플에서는 C2971를 생성 합니다.

```cpp
// C2971.cpp
template <int *pi>
class Y {};

int global_var = 0;

int main() {
   int local_var = 0;
   Y<&local_var> aY;   // C2971
   // try the following line instead
   // Y<&global_var> aY;
}
```
