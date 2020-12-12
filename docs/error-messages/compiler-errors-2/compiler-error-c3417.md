---
description: '자세한 정보: 컴파일러 오류 C3417'
title: 컴파일러 오류 C3417
ms.date: 11/04/2016
f1_keywords:
- C3417
helpviewer_keywords:
- C3417
ms.assetid: 3e7869ea-8948-42fb-ba30-6ccafe499c35
ms.openlocfilehash: d51985f619c436a1dfd6af06b97c72c3d06c7967
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321899"
---
# <a name="compiler-error-c3417"></a>컴파일러 오류 C3417

' member ': 값 형식은 사용자 정의 특수 멤버 함수를 포함할 수 없습니다.

값 형식은 기본 인스턴스 생성자, 소멸자 또는 복사 생성자와 같은 함수를 포함할 수 없습니다.

다음 샘플에서는 C3517를 생성 합니다.

```cpp
// C3417.cpp
// compile with: /clr /c
value class VC {
   VC(){}   // C3417

   // OK
   static VC(){}
   VC(int i){}
};
```
