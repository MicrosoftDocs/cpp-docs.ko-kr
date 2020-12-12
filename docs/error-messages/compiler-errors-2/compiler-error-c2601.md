---
description: '자세한 정보: 컴파일러 오류 C2601'
title: 컴파일러 오류 C2601
ms.date: 11/04/2016
f1_keywords:
- C2601
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
ms.openlocfilehash: 373ba519633034ddf63889eb82cd71dccfa4a743
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119998"
---
# <a name="compiler-error-c2601"></a>컴파일러 오류 C2601

' function ': 지역 함수 정의가 잘못 되었습니다.

코드는 함수 내에서 함수를 정의 하려고 합니다.

또는 C2601 오류의 위치 앞에 소스 코드에 추가 중괄호가 있을 수 있습니다.

다음 샘플에서는 C2601를 생성 합니다.

```cpp
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```
