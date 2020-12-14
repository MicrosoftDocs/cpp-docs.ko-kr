---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4838'
title: 컴파일러 경고 (수준 1) C4838
ms.date: 11/04/2016
f1_keywords:
- C4838
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
ms.openlocfilehash: 2676ef05934ee3c5e6afbf6df8d6d7a306db68ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197962"
---
# <a name="compiler-warning-level-1-c4838"></a>컴파일러 경고 (수준 1) C4838

' type_1 '에서 ' type_2 ' (으)로의 변환에는 축소 변환이 필요 합니다.

집계 또는 목록 초기화를 사용할 때 암시적 축소 변환을 찾았습니다.

C 언어를 사용 하면 할당 및 초기화에서 암시적 축소 변환이 가능 하 고, 예기치 않은 축소로 인해 많은 코드 오류가 발생 하는 경우에도 c + +는 그에 따라 이어집니다. 코드를 보다 안전 하 게 만들기 위해 c + + 표준에는 초기화 목록에서 축소 변환이 발생할 때 진단 메시지가 필요 합니다. Visual C++ Visual Studio 2015부터 지원 되는 균일 초기화 구문을 사용 하는 경우 진단이 [컴파일러 오류 C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md) . Visual Studio 2013에서 지 원하는 목록 또는 집계 초기화 구문을 사용 하는 경우 컴파일러는 경고를 C4838 생성 합니다.

축소 변환은 대상에 맞출 수 있는 변환 된 값의 범위를 알고 있을 때 사용할 수 있습니다. 이 경우 컴파일러에서 수행 하는 것 보다 더 많은 것을 알 수 있습니다. 축소 변환을 의도적으로 수행 하는 경우 정적 캐스트를 사용 하 여 원하는 것을 명시적으로 만듭니다. 그렇지 않으면이 경고 메시지는 거의 항상 사용자의 코드에 버그가 있음을 나타냅니다. 초기화 하는 개체에 입력을 처리할 수 있을 정도로 많은 형식이 있는지 확인 하 여 문제를 해결할 수 있습니다.

다음 샘플에서는 C4838를 생성 하 고이를 해결 하는 한 가지 방법을 보여 줍니다.

```cpp
// C4838.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C4838.cpp

struct S1 {
    int m1;
    double m2, m3;
};

void function_C4838(double d1) {
    double ad[] = { 1, d1 }; // OK
    int ai[] = { 1, d1 };    // warning C4838
    S1 s11 = { 1, 2, d1 };   // OK
    S1 s12 { d1, 2, 3 };     // warning C4838
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838
}
```
