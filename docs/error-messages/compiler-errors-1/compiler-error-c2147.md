---
description: '자세한 정보: 컴파일러 오류 C2147'
title: 컴파일러 오류 C2147
ms.date: 11/04/2016
f1_keywords:
- C2147
helpviewer_keywords:
- C2147
ms.assetid: d1adb3bf-7ece-4815-922c-ad7492fb6670
ms.openlocfilehash: 499b90ddad659a2a36652e783901b25f97eb76f4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235374"
---
# <a name="compiler-error-c2147"></a>컴파일러 오류 C2147

구문 오류: ' identifier '는 새 키워드입니다.

이제 언어의 예약 키워드 인 식별자가 사용 되었습니다.

다음 샘플에서는 C2147를 생성 합니다.

```cpp
// C2147.cpp
// compile with: /clr
int main() {
   int gcnew = 0;   // C2147
   int i = 0;   // OK
}
```
