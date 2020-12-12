---
description: '자세한 정보: 컴파일러 오류 C3553'
title: 컴파일러 오류 C3553
ms.date: 11/04/2016
f1_keywords:
- C3553
helpviewer_keywords:
- C3553
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
ms.openlocfilehash: 43e322b78bac05f6e301501a86ce7fbd2f27d285
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223219"
---
# <a name="compiler-error-c3553"></a>컴파일러 오류 C3553

> decltype에 형식이 아니라 식이 필요합니다.

`decltype()` 키워드는 형식 이름이 아니다를 인수로 식을 사용하도록 요구합니다. 예를 들어 다음 코드 조각의 마지막 문은 C3553 오류를 생성합니다.

```cpp
int x = 0;
decltype(x+1);
decltype(int); // C3553
```
