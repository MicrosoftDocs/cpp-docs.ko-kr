---
description: '자세한 정보: 함수에 대 한 Argument-Dependent Name (Koenig) 조회'
title: 함수에 대한 인수 종속 이름(Koenig) 조회
ms.date: 11/04/2016
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
ms.openlocfilehash: 726174041c919a2918687101b223f0e1cca3d5ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288193"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>함수에 대한 인수 종속 이름(Koenig) 조회

컴파일러에서는 인수 종속 이름 조회를 사용하여 정규화되지 않은 함수 호출의 정의를 찾을 수 있습니다. 인수 종속 이름 조회를 Koenig 조회라고도 합니다. 함수 호출에 있는 모든 인수의 형식은 네임스페이스, 클래스, 구조체, 공용 구조체 또는 템플릿의 계층 구조 내에서 정의됩니다. 정규화 되지 않은 [후 위](../cpp/postfix-expressions.md) 함수 호출을 지정 하는 경우 컴파일러는 각 인수 형식과 연결 된 계층에서 함수 정의를 검색 합니다.

## <a name="example"></a>예제

이 샘플에서 컴파일러는 `f()` 함수가 `x` 인수를 사용하는 것을 확인합니다. `x` 인수는 `A::X` 형식이며, 이 형식은 `A` 네임스페이스에서 정의됩니다. 컴파일러는 `A` 네임스페이스를 검색하고 `f()` 형식의 인수를 사용하는 `A::X` 함수에 대한 정의를 찾습니다.

```cpp
// argument_dependent_name_koenig_lookup_on_functions.cpp
namespace A
{
   struct X
   {
   };
   void f(const X&)
   {
   }
}
int main()
{
// The compiler finds A::f() in namespace A, which is where
// the type of argument x is defined. The type of x is A::X.
   A::X x;
   f(x);
}
```
