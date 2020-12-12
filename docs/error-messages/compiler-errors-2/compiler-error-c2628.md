---
description: '자세한 정보: 컴파일러 오류 C2628'
title: 컴파일러 오류 C2628
ms.date: 11/04/2016
f1_keywords:
- C2628
helpviewer_keywords:
- C2628
ms.assetid: 19a25e77-d5be-4107-88d5-0745b6281f98
ms.openlocfilehash: 876e96bfb406262c150807e4e95f14dd5b7177d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123567"
---
# <a name="compiler-error-c2628"></a>컴파일러 오류 C2628

' type1 ' 뒤에 ' type2 '가 올 수 없습니다. '; '이 (가) 기억나지 않습니다.

세미콜론이 없을 수 있습니다.

다음 샘플에서는 C2628를 생성 합니다.

```cpp
// C2628.cpp
class CMyClass {}
int main(){}   // C2628 error
```

해결 방법:

```cpp
// C2628b.cpp
class CMyClass {};
int main(){}
```
