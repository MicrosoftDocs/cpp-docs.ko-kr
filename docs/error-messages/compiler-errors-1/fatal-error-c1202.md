---
description: '자세한 정보: 심각한 오류 C1202'
title: 심각한 오류 C1202
ms.date: 11/04/2016
f1_keywords:
- C1202
helpviewer_keywords:
- C1202
ms.assetid: c859adb8-17a7-4fa1-a1f3-5820b7bf3849
ms.openlocfilehash: 72c7556a390c00b8e83b05c8a78535836b316318
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268108"
---
# <a name="fatal-error-c1202"></a>심각한 오류 C1202

재귀 형식 또는 함수 종속성 컨텍스트가 너무 복잡합니다.

템플릿 정의가 재귀적이거나 복잡성 제한을 초과했습니다.

## <a name="examples"></a>예제

다음 샘플에서는 C1202를 생성합니다.

```cpp
// C1202.cpp
// processor: x86 IPF
template<int n>
class Factorial : public Factorial<n-1>  {   // C1202
public:
   operator int () {
      return Factorial <n-1>::operator int () * n;
   }
};
Factorial<7> facSeven;
```

해결 방법:

```cpp
// C1202b.cpp
// compile with: /c
template<int n>
class Factorial : public Factorial<n-1> {
public:
   operator int () {
      return Factorial <n-1>::operator int () * n;
   }
};

template <>
class Factorial<0> {
public:
   operator int () {
      return 1;
   }
};

Factorial<7> facSeven;
```
