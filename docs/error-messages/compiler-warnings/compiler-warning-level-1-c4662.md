---
title: 컴파일러 경고(수준 1) C4662
ms.date: 11/04/2016
f1_keywords:
- C4662
helpviewer_keywords:
- C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
ms.openlocfilehash: 4fdb57eecb17f4385c0c297c1a13902890e16fea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175601"
---
# <a name="compiler-warning-level-1-c4662"></a>컴파일러 경고(수준 1) C4662

명시적 인스턴스화. 템플릿-클래스 'identifier1'에 'identifier2'를 특수화하는 데 사용된 정의가 없습니다.

지정된 템플릿-클래스가 선언되었지만 정의되지 않았습니다.

## <a name="example"></a>예제

```cpp
// C4662.cpp
// compile with: /W1 /LD
template<class T, int i> class MyClass; // no definition
template MyClass< int, 1>;              // C4662
```
