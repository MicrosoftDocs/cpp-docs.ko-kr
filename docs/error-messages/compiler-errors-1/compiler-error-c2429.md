---
description: '자세한 정보: 컴파일러 오류 C2429'
title: 컴파일러 오류 C2429
ms.date: 11/16/2017
f1_keywords:
- C2429
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
ms.openlocfilehash: 3c16a2a430e8050103c3903cf1355de089252ed5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190135"
---
# <a name="compiler-error-c2429"></a>컴파일러 오류 C2429

> '*language feature*'에 컴파일러 플래그 '*컴파일러 옵션*'이 필요 합니다.

언어 기능을 지원 하려면 특정 컴파일러 옵션이 필요 합니다.

오류 C2429: 언어 기능 ' 중첩 된 네임 스페이스-정의 '를 사용 하려면 Visual Studio 2015 업데이트 5에서 시작 하 여 하나 이상의 범위에 중첩 된 네임 스페이스 이름을 포함 하는 네임 스페이스인 *복합 네임* 스페이스를 정의 하려고 할 경우 **컴파일러 플래그 '/std: c + + 17 '** 이 생성 됩니다. Visual Studio 2017 버전 15.3에서는 **/std: c + + 최신** 스위치가 필요 합니다. C + + 17 이전에는 c + +에서 복합 네임 스페이스 정의를 사용할 수 없습니다. [/Od: c + + 17](../../build/reference/std-specify-language-standard-version.md) 컴파일러 옵션이 지정 된 경우 컴파일러는 복합 네임 스페이스 정의를 지원 합니다.

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual Studio 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
