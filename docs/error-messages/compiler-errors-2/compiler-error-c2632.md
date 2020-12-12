---
description: '자세한 정보: 컴파일러 오류 C2632'
title: 컴파일러 오류 C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: b6f1091b512d3a01efa933c998bde3d0885bbff1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123515"
---
# <a name="compiler-error-c2632"></a>컴파일러 오류 C2632

' type1 ' 뒤에 ' type2 '가 올 수 없습니다.

두 형식 지정자 사이에 누락 된 코드가 있는 경우이 오류가 발생할 수 있습니다.

다음 샘플에서는 C2632를 생성 합니다.

```cpp
// C2632.cpp
int float i;   // C2632
```

이 오류는 Visual Studio .NET 2003에 대해 수행 된 컴파일러 규칙 작업의 결과로도 생성 될 수 있습니다. **`bool`** 는 이제 적절 한 형식입니다. 이전 버전에서는 **`bool`** typedef 이며 해당 이름을 사용 하 여 식별자를 만들 수 있습니다.

다음 샘플에서는 C2632를 생성 합니다.

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

이 오류를 해결 하려면 Visual Studio .NET 2003 및 Visual Studio .NET 버전 Visual C++ 모두에서 코드가 유효 하도록 식별자의 이름을 바꿉니다.
