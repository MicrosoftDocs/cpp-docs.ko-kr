---
description: '자세한 정보: 컴파일러 오류 C2998'
title: 컴파일러 오류 C2998
ms.date: 11/04/2016
f1_keywords:
- C2998
helpviewer_keywords:
- C2998
ms.assetid: 8193d491-b5d9-4477-acb1-cf166889c070
ms.openlocfilehash: 43370ee8659335f6d14a2850ba0b874434786ca0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253613"
---
# <a name="compiler-error-c2998"></a>컴파일러 오류 C2998

'identifier': 템플릿 정의일 수 없습니다.

컴파일러에서 템플릿 정의에 사용되는 구문을 처리할 수 없습니다.

다음 샘플에서는 C2998을 생성합니다.

```cpp
// C2998.cpp
// compile with: /c
template <class T> int x = 1018; // C2998
```
