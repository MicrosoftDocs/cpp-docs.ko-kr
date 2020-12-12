---
description: '자세한 정보: 컴파일러 오류 C2947'
title: 컴파일러 오류 C2947
ms.date: 11/04/2016
f1_keywords:
- C2947
helpviewer_keywords:
- C2947
ms.assetid: 6c056f62-ec90-4883-8a67-aeeb6ec13546
ms.openlocfilehash: 5b1780d49f97bfab33e70a4dd7b1958b56c8df14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189485"
---
# <a name="compiler-error-c2947"></a>컴파일러 오류 C2947

구문을 종료 하려면 ' > '이 필요 합니다. ' 구문 '이 있습니다.

제네릭 또는 템플릿 인수 목록이 제대로 종료 되지 않았을 수 있습니다.

C2947는 구문 오류에 의해 생성 될 수도 있습니다.

다음 샘플에서는 C2947를 생성 합니다.

```cpp
// C2947.cpp
// compile with: /c
template <typename T>=   // C2947
// try the following line instead
// template <typename T>
struct A {};
```
