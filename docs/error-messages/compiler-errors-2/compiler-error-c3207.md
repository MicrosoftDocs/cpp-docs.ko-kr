---
description: '자세한 정보: 컴파일러 오류 C3207'
title: 컴파일러 오류 C3207
ms.date: 11/04/2016
f1_keywords:
- C3207
helpviewer_keywords:
- C3207
ms.assetid: 4a28b976-142a-4cff-aa2f-480b892c50ca
ms.openlocfilehash: 744dbee62e6247b07ca07354c44d4ebb7a438766
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173989"
---
# <a name="compiler-error-c3207"></a>컴파일러 오류 C3207

'function': 'arg'에 대한 템플릿 인수가 잘못되었습니다. 클래스 템플릿이 필요합니다.

템플릿 함수가 템플릿 인수를 사용하도록 정의되어 있습니다. 그러나 템플릿 형식 인수가 전달되었습니다.

다음 샘플에서는 C3207을 생성합니다.

```cpp
// C3207.cpp
template <template <class T> class TT>
void f(){}

template <class T>
struct S
{
};

void f1()
{
   f<S<int> >();   // C3207
   // try the following line instead
   // f<S>();
}
```
