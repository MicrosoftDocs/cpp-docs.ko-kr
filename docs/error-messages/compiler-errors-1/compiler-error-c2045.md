---
description: '자세한 정보: 컴파일러 오류 C2045'
title: 컴파일러 오류 C2045
ms.date: 11/04/2016
f1_keywords:
- C2045
helpviewer_keywords:
- C2045
ms.assetid: 2fca668e-9b20-4933-987a-18c0fd0187df
ms.openlocfilehash: 878ae18a20bbaa0da7219e2a68f8772c5dd0a637
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175172"
---
# <a name="compiler-error-c2045"></a>컴파일러 오류 C2045

'identifier': 레이블이 재정의되었습니다.

레이블이 같은 함수의 여러 문 앞에 나타납니다.

다음 샘플에서는 C2045를 생성합니다.

```cpp
// C2045.cpp
int main() {
   label: {
   }
   goto label;
   label: {}   // C2045
}
```
