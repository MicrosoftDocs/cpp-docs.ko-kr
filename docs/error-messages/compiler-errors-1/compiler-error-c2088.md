---
description: '자세한 정보: 컴파일러 오류 C2088'
title: 컴파일러 오류 C2088
ms.date: 11/04/2016
f1_keywords:
- C2088
helpviewer_keywords:
- C2088
ms.assetid: b93f7094-185b-423d-8bb9-507cd757dbf5
ms.openlocfilehash: 246c130c0918310b59924f3940950d443c0b9217
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251923"
---
# <a name="compiler-error-c2088"></a>컴파일러 오류 C2088

' operator ': ' 클래스 키 '의 경우 잘못 되었습니다.

구조체 또는 공용 구조체에 대 한 연산자가 정의 되지 않았습니다. 이 오류는 C 코드에 대해서만 유효 합니다.

다음 샘플에서는 C2088를 세 번 생성 합니다.

```c
// C2088.c
struct S {
   int m_i;
} s;

int main() {
   int i = s * 1;   // C2088
   struct S s2 = +s;   // C2088
   s++;   // C2088
}
```
