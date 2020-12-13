---
description: '자세한 정보: 컴파일러 오류 C3858'
title: 컴파일러 오류 C3858
ms.date: 11/04/2016
f1_keywords:
- C3858
helpviewer_keywords:
- C3858
ms.assetid: 46e178d5-a55f-4ac6-a9dc-561fbcba5c1f
ms.openlocfilehash: 16547372e30d20f961f1c7f011894b021d96d587
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336126"
---
# <a name="compiler-error-c3858"></a>컴파일러 오류 C3858

' type ': 현재 범위에서 다시 선언할 수 없습니다.

동일한 범위에서 형식을 두 번 선언할 수 없습니다.

다음 샘플에서는 C3858를 생성 합니다.

```cpp
// C3858.cpp
// compile with: /LD
template <class T>
struct Outer
{
   struct Inner;
};

template <class T>
struct Outer<T>::Inner;   // C3858
// try the following line instead
// struct Outer<T>::Inner{};
```
