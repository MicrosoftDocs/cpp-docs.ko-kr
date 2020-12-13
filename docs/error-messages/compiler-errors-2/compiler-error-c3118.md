---
description: '자세한 정보: 컴파일러 오류 C3118'
title: 컴파일러 오류 C3118
ms.date: 11/04/2016
f1_keywords:
- C3118
helpviewer_keywords:
- C3118
ms.assetid: 40fbe681-8868-4cb2-a2b2-4db4449319a7
ms.openlocfilehash: cc6d9c446603adaa314480f8f18ae8bd2c168277
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151101"
---
# <a name="compiler-error-c3118"></a>컴파일러 오류 C3118

' interface ': 인터페이스가 가상 상속을 지원 하지 않습니다.

인터페이스에서 실질적으로 상속 하려고 했습니다. 예를 들면 다음과 같습니다.

```cpp
// C3118.cpp
__interface I1 {
};

__interface I2 : virtual I1 {   // C3118
};
```

이 오류를 생성 합니다.
