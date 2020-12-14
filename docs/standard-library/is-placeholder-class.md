---
description: Is_placeholder 클래스에 대해 자세히 알아보세요.
title: is_placeholder 클래스
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_placeholder
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
ms.openlocfilehash: 84d73da6ffe2446a8448b0ff5f30604d259493b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230655"
---
# <a name="is_placeholder-class"></a>is_placeholder 클래스

형식이 자리 표시자인지 테스트합니다.

## <a name="syntax"></a>Syntax

구조체 is_placeholder {static const int value;};

## <a name="remarks"></a>설명

`Ty` 형식이 자리 표시자가 아니면 상수 값 `value`는 0이고, 그렇지 않으면 해당 값은 바인딩된 함수 호출 인수의 위치입니다. N번째 자리 표시자 `_N`에 대해 `N` 값을 확인하는 데 사용됩니다.

## <a name="example"></a>예제

```cpp
// std__functional__is_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

using namespace std::placeholders;

template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}
```

```Output
0
3
```
