---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4103'
title: 컴파일러 경고 (수준 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: 98a9cfbda60ccc938f2cda7803fcdf7e996def9f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272229"
---
# <a name="compiler-warning-level-1-c4103"></a>컴파일러 경고 (수준 1) C4103

' filename ': 헤더를 포함 한 후 맞춤이 변경 되었습니다. pop (#pragma 팩이 누락 되었기 때문일 수 있습니다.

압축은 클래스의 레이아웃에 영향을 주며 일반적으로 헤더 파일에서 변경 내용을 압축 하는 경우 문제가 발생할 수 있습니다.

헤더 파일을 끝내기 전에 pop (#pragma [pack](../../preprocessor/pack.md))를 사용 하 여이 경고를 해결 하십시오.

다음 샘플에서는 C4103를 생성 합니다.

```cpp
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

그리고

```cpp
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```
