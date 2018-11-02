---
title: C++의 선언 지점
ms.date: 11/04/2016
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
ms.openlocfilehash: d6cb4c3813d88c8b29fbcb2e0827805f406e6c81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560656"
---
# <a name="point-of-declaration-in-c"></a>C++의 선언 지점

선언자 바로 뒤, 이니셜라이저 앞(선택 사항)에서 이름이 선언된다고 간주합니다. (참조 선언 자에 대 한 자세한 내용은 [선언 및 정의](declarations-and-definitions-cpp.md).)

다음 예제를 고려해 보세요.

```cpp
// point_of_declaration1.cpp
// compile with: /W1
double dVar = 7.0;
int main()
{
   double dVar = dVar;   // C4700
}
```

선언 지점 되었으면 *후* 를 초기화 하는 다음 로컬 `dVar` 7.0, 전역 변수의 값으로 초기화할 수는 `dVar`합니다. 그러나 그런 경우는 아니므로 `dVar`이 정의되지 않은 값으로 초기화됩니다.

## <a name="see-also"></a>참고자료

[범위](../cpp/scope-visual-cpp.md)