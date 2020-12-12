---
description: '자세한 정보: 컴파일러 오류 C2736'
title: 컴파일러 오류 C2736
ms.date: 11/04/2016
f1_keywords:
- C2736
helpviewer_keywords:
- C2736
ms.assetid: 95a6bc28-c0cb-49dc-87e6-e993dbbba881
ms.openlocfilehash: 635f20d684fb929277f29299f0f074cc3a19e9df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123164"
---
# <a name="compiler-error-c2736"></a>컴파일러 오류 C2736

캐스트에는 ' keyword ' 키워드를 사용할 수 없습니다.

캐스트에서 키워드를 사용할 수 없습니다.

다음 샘플에서는 C2736를 생성 합니다.

```cpp
// C2736.cpp
int main() {
   return (virtual) 0;   // C2736
   // try the following line instead
   // return 0;
}
```
