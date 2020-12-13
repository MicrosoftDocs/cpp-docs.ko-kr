---
description: '자세한 정보: 컴파일러 오류 C2117'
title: 컴파일러 오류 C2117
ms.date: 11/04/2016
f1_keywords:
- C2117
helpviewer_keywords:
- C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
ms.openlocfilehash: 0e0d84a73d5f36f3014aa07d51b9701276a6e071
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335253"
---
# <a name="compiler-error-c2117"></a>컴파일러 오류 C2117

' identifier ': 배열 범위 오버플로입니다.

배열에 이니셜라이저가 너무 많습니다.

- 배열 요소와 이니셜라이저가 크기와 수량에서 일치 하지 않습니다.

- 문자열에 null 종결자를 위한 공간이 없습니다.

다음 샘플에서는 C2117를 생성 합니다.

```cpp
// C2117.cpp
int main() {
   char abc[4] = "abcd";   // C2117
   char def[4] = "abd";   // OK
}
```
