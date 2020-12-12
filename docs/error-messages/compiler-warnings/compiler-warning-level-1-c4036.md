---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4036'
title: 컴파일러 경고(수준 1) C4036
ms.date: 11/04/2016
f1_keywords:
- C4036
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
ms.openlocfilehash: 6547cd068b39ff3db54829dfc20fb47a52113e2a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318925"
---
# <a name="compiler-warning-level-1-c4036"></a>컴파일러 경고(수준 1) C4036

실제 매개 변수로 명명되지 않은 'type'입니다.

실제 매개 변수로 사용하는 구조체, 공용 구조체, 열거형 또는 클래스에 대해 형식 이름이 지정되지 않았습니다. 함수 프로토타입을 생성하는 데 [/Zg](../../build/reference/zg-generate-function-prototypes.md) 를 사용하고 있는 경우 컴파일러에서 이 경고를 발생시키고 생성된 프로토타입에서 정식 매개 변수를 주석으로 처리합니다.

이 경고를 해결하려면 형식 이름을 지정합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4036을 생성합니다.

```c
// C4036.c
// compile with: /Zg /W1
// D9035 expected
typedef struct { int i; } T;
void f(T* t) {}   // C4036

// OK
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```
