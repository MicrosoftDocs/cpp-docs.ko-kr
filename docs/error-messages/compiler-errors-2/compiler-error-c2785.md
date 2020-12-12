---
description: '자세한 정보: 컴파일러 오류 C2785'
title: 컴파일러 오류 C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: f40b652e30b30f0ef17426b547337352181383e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297904"
---
# <a name="compiler-error-c2785"></a>컴파일러 오류 C2785

' 1 ' 및 ' declaration2 '의 반환 형식이 다릅니다.

함수 템플릿 특수화의 반환 형식은 기본 함수 템플릿의 반환 형식과 다릅니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 일관성을 위해 함수 템플릿의 모든 특수화를 확인 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2785를 생성 합니다.

```cpp
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```
