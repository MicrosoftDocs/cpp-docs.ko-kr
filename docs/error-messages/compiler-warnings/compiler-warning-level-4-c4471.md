---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4471'
title: 컴파일러 경고 (수준 4) C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: cef492bf8aab33f46b3f590a13ffa5462a7ca41d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203499"
---
# <a name="compiler-warning-level-4-c4471"></a>컴파일러 경고 (수준 4) C4471

'*enumeration*': 범위가 없는 열거형의 전방 선언에는 내부 형식이 있어야 합니다 (int로 가정).

기본 형식에 대 한 지정자 없이 범위가 지정 되지 않은 열거형의 전방 선언을 찾았습니다. 기본적으로 Visual C++ **`int`** 는 열거형의 기본 형식으로 가정 합니다. 이로 인해 열거형 정의에 다른 형식이 사용 된 경우, 예를 들어 다른 명시적 형식이 지정 된 경우 또는 이니셜라이저가 암시적으로 다른 형식이 암시적으로 설정 된 경우 문제가 발생할 수 있습니다. 이식성 문제가 있을 수도 있습니다. 다른 컴파일러 **`int`** 는 열거형의 기본 형식 이라고 가정 하지 않습니다.

이 경고는 기본적으로 해제 되어 있습니다. /Wall 또는/w *N* 4471을 사용 하 여 명령줄에서 사용 하도록 설정 하거나 소스 파일에 #pragma [경고](../../preprocessor/warning.md) 를 사용할 수 있습니다.

## <a name="examples"></a>예제

경우에 따라이 경고는 의사입니다. 열거형에 대 한 전방 선언이 정의 뒤에 표시 되는 경우이 경고가 발생할 수 있습니다. 예를 들어이 코드는 C4471를 발생 시킬 수 있는 경우에도 유효 합니다.

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

일반적으로 전방 선언 대신 범위가 없는 열거형에 전체 정의를 사용 하는 것이 안전 합니다. 정의를 헤더 파일에 배치 하 고이를 참조 하는 소스 파일에 포함할 수 있습니다. 이는 c + + 98 이상용으로 작성 된 코드에서 작동 합니다. 이식성 및 유지 관리 용이성을 위해이 솔루션을 권장 합니다.

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

C + + 11에서는 범위가 없는 열거형 및 전방 선언에 명시적 형식을 추가할 수 있습니다. 복합 헤더 포함 논리가 전방 선언 대신 정의를 사용할 수 없는 경우에만이 솔루션을 사용 하는 것이 좋습니다. 이 솔루션을 사용 하면 유지 관리 문제가 발생할 수 있습니다. 열거형 정의에 사용 되는 기본 형식을 변경 하는 경우에는 모든 전방 선언이 일치 하도록 변경 해야 합니다. 그렇지 않으면 코드에서 자동 오류가 발생할 수 있습니다. 이 문제를 최소화 하기 위해 전방 선언을 헤더 파일에 넣을 수 있습니다.

```cpp
// C4471c.cpp
// Client code for enumeration defined in C4471d.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example;    // C4471, int assumed
// To fix, replace the lines above with the forward declarations:
// enum Example : unsigned;
// ...
```

```cpp
// C4471d.cpp
// Definition for enumeration used in C4471c.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example : unsigned { item = 0x80000000 }; // explicit type
// ...
```

열거형에 명시적 형식을 지정 하는 경우 기본적으로 설정 되는 경고 [C4369](compiler-warning-level-1-C4369.md)사용 하도록 설정 하는 것이 좋습니다. 이는 열거형 항목에 명시적으로 지정 된 형식과 다른 형식이 필요한 경우를 식별 합니다.

C + + 11의 새로운 기능인 범위가 지정 된 열거형을 사용 하도록 코드를 변경할 수 있습니다. 열거형을 사용 하는 정의와 클라이언트 코드는 모두 범위가 지정 된 열거형을 사용 하도록 변경 해야 합니다. 네임 스페이스 오염에 문제가 있는 경우 정의 된 열거 항목의 이름이 열거형의 범위로 제한 되므로 범위가 지정 된 열거형을 사용 하는 것이 좋습니다. 범위가 지정 된 열거형의 또 다른 특징은 해당 멤버를 다른 정수 계열 또는 열거형 형식으로 암시적으로 변환할 수 없다는 것입니다 .이는 미묘한 버그의 소스가 될 수 있습니다.

```cpp
// C4471e.cpp
// Client code for scoped enumeration defined in C4471f.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum Example;    // C4471
// To fix, replace the line above with the forward declaration:
// enum class Example;
// ...
```

```cpp
// C4471f.cpp
// Definition for scoped enumeration used in C4471e.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum class Example { item = 0 };
// ...
```
