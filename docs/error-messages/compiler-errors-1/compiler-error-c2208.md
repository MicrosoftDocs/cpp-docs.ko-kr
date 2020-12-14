---
description: '자세한 정보: 컴파일러 오류 C2208'
title: 컴파일러 오류 C2208
ms.date: 11/04/2016
f1_keywords:
- C2208
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
ms.openlocfilehash: 76452c504e5f90857b15c5fc9250923705d3d20c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245644"
---
# <a name="compiler-error-c2208"></a>컴파일러 오류 C2208

' type ':이 형식을 사용 하 여 정의 된 멤버가 없습니다.

형식 이름으로 확인 하는 식별자는 집계 선언에 있지만 컴파일러에서 멤버를 선언할 수 없습니다.

다음 샘플에서는 C2208를 생성 합니다.

```cpp
// C2208.cpp
class C {
   C;   // C2208
   C(){}   // OK
};
```
