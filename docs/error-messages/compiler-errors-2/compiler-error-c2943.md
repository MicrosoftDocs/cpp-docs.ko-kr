---
description: '자세한 정보: 컴파일러 오류 C2943'
title: 컴파일러 오류 C2943
ms.date: 11/04/2016
f1_keywords:
- C2943
helpviewer_keywords:
- C2943
ms.assetid: ede6565e-d892-44c0-8eee-c69545f3be2e
ms.openlocfilehash: f85000ae554e25f2ca783b605b036abb3f04eadb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249583"
---
# <a name="compiler-error-c2943"></a>컴파일러 오류 C2943

'class': type-class-id가 템플릿의 형식 인수로 재정의되었습니다.

제네릭 또는 템플릿 클래스를 기호 대신 제네릭 또는 템플릿 형식 인수로 사용할 수 없습니다.

다음 샘플에서는 C2943을 생성합니다.

```cpp
// C2943.cpp
// compile with: /c
template<class T>
class List {};

template<class List<int> > class MyList;   // C2943
template<class T >  class MyList;
```
