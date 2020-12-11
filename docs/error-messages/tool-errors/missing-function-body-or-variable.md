---
description: '자세한 정보: 함수 본문 또는 변수 누락'
title: 함수 본문 또는 변수 누락
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 6a4349c380fc0f573adc8e372f9e4d2fc3f83873
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155165"
---
# <a name="missing-function-body-or-variable"></a>함수 본문 또는 변수 누락

함수 프로토타입을 사용 하는 경우 컴파일러는 오류 없이 계속 될 수 있지만 함수 코드 또는 예약 된 가변 공간이 없기 때문에 링커에서 주소에 대 한 호출을 확인할 수 없습니다. 링커가 확인 해야 하는 함수에 대 한 호출을 만들 때까지이 오류가 표시 되지 않습니다.

## <a name="example-call-to-an-undefined-function"></a>예제: 정의 되지 않은 함수 호출

프로토타입이 있으면 컴파일러가 함수를 사용할 수 있다고 생각할 수 있으므로 main의 함수 호출은 LNK2019를 발생 시킵니다.  링커가이를 찾지 못합니다.

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example-call-to-an-implemented-function"></a>예: 구현 된 함수 호출

C + +에서는 클래스 정의의 프로토타입이 아니라 클래스에 대 한 특정 함수 구현을 포함 하는지 확인 합니다. 헤더 파일 외부에 클래스를 정의 하는 경우에는 함수 () 앞에 클래스 이름을 포함 해야 `Classname::memberfunction` 합니다.

```cpp
// LNK2019_MFBV_2.cpp
// LNK2019 expected
struct A {
   static void Test();
};

// Should be void A::Test() {}
void Test() {}

int main() {
   A AObject;
   AObject.Test();
}
```

## <a name="see-also"></a>참고 항목

[링커 도구 오류 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
