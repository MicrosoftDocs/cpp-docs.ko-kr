---
description: '자세한 정보: 컴파일러 오류 C3768'
title: 컴파일러 오류 C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: 3203fe74fb1da91f24312f76ca11ac49711da8f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291716"
---
# <a name="compiler-error-c3768"></a>컴파일러 오류 C3768

> 순수 관리 코드에서는 가상 vararg 함수의 주소를 가져올 수 없습니다.

## <a name="remarks"></a>설명

**/Clr: pure** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

**/Clr: pure** 를 사용 하 여 컴파일하는 경우 가상 함수의 주소를 가져올 수 없습니다 `vararg` .

## <a name="example"></a>예제

다음 샘플에서는 C3768를 생성 합니다.

```cpp
// C3768.cpp
// compile with: /clr:pure
struct A
{
   virtual void f(...);
};

int main()
{
   &(A::f);   // C3768
}
```
