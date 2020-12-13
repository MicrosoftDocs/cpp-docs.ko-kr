---
description: '자세한 정보: 컴파일러 오류 C2397'
title: 컴파일러 오류 C2397
ms.date: 11/04/2016
f1_keywords:
- C2397
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
ms.openlocfilehash: 8e5f000b8d0881fd6a57bb4895afbdef0e7c598a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145381"
---
# <a name="compiler-error-c2397"></a>컴파일러 오류 C2397

' type_1 '에서 ' type_2 ' (으)로의 변환에는 축소 변환이 필요 합니다.

균일 초기화를 사용 하는 경우 암시적 축소 변환을 찾았습니다.

C 언어를 사용 하면 할당 및 초기화에서 암시적 축소 변환이 가능 하 고, 예기치 않은 축소로 인해 많은 코드 오류가 발생 하는 경우에도 c + +는 그에 따라 이어집니다. 코드를 보다 안전 하 게 만들기 위해 c + + 표준에는 초기화 목록에서 축소 변환이 발생할 때 진단 메시지가 필요 합니다. Visual C++ Visual Studio 2015부터 지원 되는 균일 초기화 구문을 사용 하는 경우 진단이 컴파일러 오류 C2397. Visual Studio 2013에서 지 원하는 목록 또는 집계 초기화 구문을 사용 하는 경우 컴파일러에서 [컴파일러 경고 (수준 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) 를 생성 합니다.

축소 변환은 대상에 맞출 수 있는 변환 된 값의 범위를 알고 있을 때 사용할 수 있습니다. 이 경우 컴파일러에서 수행 하는 것 보다 더 많은 것을 알 수 있습니다. 축소 변환을 의도적으로 수행 하는 경우 정적 캐스트를 사용 하 여 원하는 것을 명시적으로 만듭니다. 그렇지 않으면이 오류 메시지는 거의 항상 코드에 버그가 있음을 나타냅니다. 초기화 하는 개체에 입력을 처리할 수 있을 정도로 많은 형식이 있는지 확인 하 여 문제를 해결할 수 있습니다.

다음 샘플에서는 C2397를 생성 하 고이를 해결 하는 한 가지 방법을 보여 줍니다.

```
// C2397.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C2397.cpp
#include <vector>

struct S1 {
    int m1;
    double m2, m3;
};

void function_C2397(double d1) {
    char c1 { 127 };          // OK
    char c2 { 513 };          // error C2397

    std::vector<S1> vS1;
    vS1.push_back({ d1, 2, 3 }); // error C2397

    // Possible fix if you know d1 always fits in an int
    vS1.push_back({ static_cast<int>(d1), 2, 3 });
}
```
