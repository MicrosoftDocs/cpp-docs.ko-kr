---
description: '자세한 정보: 컴파일러 오류 C2299'
title: 컴파일러 오류 C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: eb96829c4e16153a0a304a5b2a9640d4591dec3f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235101"
---
# <a name="compiler-error-c2299"></a>컴파일러 오류 C2299

' function ': 동작 변경: 명시적 특수화는 복사 생성자 또는 복사 할당 연산자가 될 수 없습니다.

이 오류는 Visual Studio 2005에 대해 수행한 컴파일러 규칙 작업의 결과로 생성 될 수도 있습니다. 이전 버전의 Visual C++ 복사 생성자 또는 복사 할당 연산자에 대해 명시적 특수화를 허용 했습니다.

C2299를 해결 하려면 복사 생성자 또는 할당 연산자를 템플릿 함수로 지정 하지 말고 클래스 형식을 사용 하는 비템플릿 함수를 사용 합니다. 템플릿 인수를 명시적으로 지정 하 여 복사 생성자 또는 대입 연산자를 호출 하는 모든 코드는 템플릿 인수를 제거 해야 합니다.

다음 샘플에서는 C2299를 생성 합니다.

```cpp
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```
