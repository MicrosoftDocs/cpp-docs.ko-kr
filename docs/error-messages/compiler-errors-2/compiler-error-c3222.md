---
description: '자세한 정보: 컴파일러 오류 C3222'
title: 컴파일러 오류 C3222
ms.date: 11/04/2016
f1_keywords:
- C3222
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
ms.openlocfilehash: 77883b6bd9be034fff2a0bcf3babdb1489c9a937
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267718"
---
# <a name="compiler-error-c3222"></a>컴파일러 오류 C3222

'parameter': 제네릭 함수 또는 관리되는 또는 WinRT 형식의 멤버 함수에 대한 기본 인수를 선언할 수 없습니다.

기본 인수를 사용하는 메서드 매개 변수를 선언할 수 없습니다. 메서드의 오버로드된 형식은 이 문제를 해결하는 한 가지 방법입니다. 즉, 매개 변수 없이 동일한 이름을 사용하는 메서드를 정의한 다음 메서드 본문에서 변수를 초기화합니다.

다음 샘플에서는 C3222를 생성합니다.

```cpp
// C3222_2.cpp
// compile with: /clr
public ref class G {
   void f( int n = 0 );   // C3222
};
```
