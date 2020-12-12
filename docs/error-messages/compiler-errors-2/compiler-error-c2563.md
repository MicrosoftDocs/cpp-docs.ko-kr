---
description: '자세한 정보: 컴파일러 오류 C2563'
title: 컴파일러 오류 C2563
ms.date: 11/04/2016
f1_keywords:
- C2563
helpviewer_keywords:
- C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
ms.openlocfilehash: 2243e0820b2e69d6bc05351fdba4600188a3ac08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209154"
---
# <a name="compiler-error-c2563"></a>컴파일러 오류 C2563

정식 매개 변수 목록의 불일치

함수의 형식 매개 변수 목록 (또는 함수에 대 한 포인터)이 다른 함수 또는 멤버 함수에 대 한 포인터와 일치 하지 않습니다. 따라서 함수 또는 포인터를 할당할 수 없습니다.

다음 샘플에서는 C2563를 생성 합니다.

```cpp
// C2563.cpp
void func( int );
void func( int, int );
int main() {
   void *fp();
   fp = func;   // C2563
}
```
