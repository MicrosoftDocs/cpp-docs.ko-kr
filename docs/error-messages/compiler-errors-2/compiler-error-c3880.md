---
description: '자세한 정보: 컴파일러 오류 C3880'
title: 컴파일러 오류 C3880
ms.date: 11/04/2016
f1_keywords:
- C3880
helpviewer_keywords:
- C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
ms.openlocfilehash: c2d279cd50716f647fbbdf51f9f9c39863d4e2d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274595"
---
# <a name="compiler-error-c3880"></a>컴파일러 오류 C3880

' var ': 리터럴 데이터 멤버일 수 없습니다.

[리터럴](../../extensions/literal-cpp-component-extensions.md) 특성의 형식은 다음 형식 중 하나인 또는로 변환할 수 있는 컴파일 시간 이어야 합니다.

- 정수 계열 형식

- 문자열

- 정수 계열 또는 기본 형식을 사용 하는 열거형

다음 샘플에서는 C3880를 생성 합니다.

```cpp
// C3880.cpp
// compile with: /clr /c
ref struct Y1 {
   literal System::Decimal staticConst1 = 10;   // C3880
   literal int staticConst2 = 10;   // OK
};
```
