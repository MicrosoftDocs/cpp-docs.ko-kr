---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4067'
title: 컴파일러 경고 (수준 1) C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: b11167ba5648e71be16197ecfb418d92cb5d879a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267666"
---
# <a name="compiler-warning-level-1-c4067"></a>컴파일러 경고 (수준 1) C4067

> 전처리기 지시문 뒤에 예기치 않은 토큰이 있습니다. 줄 바꿈이 필요 합니다.

## <a name="remarks"></a>설명

컴파일러가 전처리기 지시문 뒤에 추가 문자를 발견 하 고 무시 했습니다. 이는 예기치 않은 문자로 인해 발생할 수 있지만 일반적인 원인은 지시문 뒤에는 흩어진 세미콜론이 있습니다. 주석은이 경고를 발생 시 키 지 않습니다. **/Za** 컴파일러 옵션을 사용 하면 기본 설정 보다 전처리기 지시문을 더 많이 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// C4067a.cpp
// compile with: cl /EHsc /DX /W1 /Za C4067a.cpp
#include <iostream>
#include <string> s     // C4067
#if defined(X);         // C4067
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif;                 // C4067 only under /Za
int main()
{
    std::cout << s << std::endl;
}
```

이 경고를 해결 하려면 흩어진 문자를 삭제 하거나 주석 블록으로 이동 합니다. **/Za** 컴파일러 옵션을 제거 하 여 특정 C4067 경고를 사용 하지 않도록 설정할 수 있습니다.

```cpp
// C4067b.cpp
// compile with: cl /EHsc /DX /W1 C4067b.cpp
#include <iostream>
#include <string>
#if defined(X)
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif
int main()
{
    std::cout << s << std::endl;
}
```
