---
description: '자세한 정보: 컴파일러 오류 C3279'
title: 컴파일러 오류 C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: c257a97cad1603703e7dbf2ed0d9f5cb3e6134a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258020"
---
# <a name="compiler-error-c3279"></a>컴파일러 오류 C3279

cli 네임스페이스에 선언된 클래스 템플릿의 명시적 인스턴스화 및 부분/명시적 특수화는 허용되지 않습니다.

`cli` 네임스페이스는 Microsoft에 의해 정의되며 의사(pseudo) 템플릿을 포함합니다. Microsoft c + + 컴파일러는이 네임 스페이스에서 사용자 정의, 부분 및 명시적 특수화와 클래스 템플릿의 명시적 인스턴스화를 허용 하지 않습니다.

다음 샘플에서는 C3279를 생성합니다.

```cpp
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```
