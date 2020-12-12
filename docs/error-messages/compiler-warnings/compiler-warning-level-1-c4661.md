---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4661'
title: 컴파일러 경고(수준 1) C4661
ms.date: 11/04/2016
f1_keywords:
- C4661
helpviewer_keywords:
- C4661
ms.assetid: 603bb8b7-356d-4eef-924b-64d769bac5bd
ms.openlocfilehash: 401f9a7229b4eec1f6484c49b6d2b1a18d8c49f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318834"
---
# <a name="compiler-warning-level-1-c4661"></a>컴파일러 경고(수준 1) C4661

' identifier ': 명시적 템플릿 인스턴스화 요청에 적합 한 정의가 제공 되지 않았습니다.

템플릿 클래스의 멤버가 정의 되어 있지 않습니다.

## <a name="example"></a>예제

```cpp
// C4661.cpp
// compile with: /W1 /LD
template<class T> class MyClass {
public:
   void i();   // declaration but not definition
};
template MyClass< int >;  // C4661
```
