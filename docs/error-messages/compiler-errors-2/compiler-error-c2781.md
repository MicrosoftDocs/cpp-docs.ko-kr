---
description: '자세한 정보: 컴파일러 오류 C2781'
title: 컴파일러 오류 C2781
ms.date: 11/04/2016
f1_keywords:
- C2781
helpviewer_keywords:
- C2781
ms.assetid: f29b9963-f55b-427c-8db6-50f37713df5a
ms.openlocfilehash: 9d99353b808494b20007784dd6016097afc783d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298008"
---
# <a name="compiler-error-c2781"></a>컴파일러 오류 C2781

' 선언 ': 하나 이상의 value1 인수가 필요 합니다. value2가 제공 되었습니다.

가변 매개 변수 목록을 사용 하는 함수 템플릿에 인수가 너무 적습니다.

다음 샘플에서는 C2781를 생성 합니다.

```cpp
// C2781.cpp
template<typename T>
void f(T, T, ...){}

int main() {
   f(1);   // C2781

   // try the following line instead
   f(1,1);
}
```
