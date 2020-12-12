---
description: '자세한 정보: 컴파일러 오류 C2917'
title: 컴파일러 오류 C2917
ms.date: 11/04/2016
f1_keywords:
- C2917
helpviewer_keywords:
- C2917
ms.assetid: ec9da9ee-0f37-47b3-87dd-19ef5a14dc4c
ms.openlocfilehash: c860ee47ae46db5667f39014b2f504f8f6d08e51
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270435"
---
# <a name="compiler-error-c2917"></a>컴파일러 오류 C2917

'name': 템플릿-매개 변수가 잘못되었습니다.

템플릿 매개 변수 목록에 템플릿 매개 변수가 아닌 식별자가 포함되어 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2917을 생성합니다.

```cpp
// C2917.cpp
// compile with: /c
template<class T> class Vector {
   void sort();
};

template<class T*> void Vector<T>::sort() {}   // C2917
// try the following line instead
// template<class T> void Vector<T>::sort() {}
```
