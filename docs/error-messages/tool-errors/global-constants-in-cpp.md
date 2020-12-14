---
description: '자세한 정보: c + +의 전역 상수'
title: C++의 전역 상수
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 8e960e7e10942fc231fcdeafef6e8d755694c460
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261660"
---
# <a name="global-constants-in-c"></a>C++의 전역 상수

C + + 전역 상수에는 정적 링크가 있습니다. 이는 C와는 다릅니다. 여러 파일에서 c + +로 전역 상수를 사용 하려고 하면 확인 되지 않은 외부 오류가 발생 합니다. 컴파일러가 전역 상수를 최적화 하 여 변수에 예약 된 공간을 남겨 두지 않습니다.

이 오류를 해결 하는 한 가지 방법은 헤더 파일에 const 초기화를 포함 하 고 필요한 경우 해당 헤더를 CPP 파일에 포함 하는 것입니다 (함수 프로토타입 처럼). 또 다른 가능성은 변수를 비상수로 만들고이를 평가할 때 상수 참조를 사용 하는 것입니다.

다음 샘플에서는 C2019를 생성 합니다.

```cpp
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

그리고

```cpp
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>참고 항목

[링커 도구 오류 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
