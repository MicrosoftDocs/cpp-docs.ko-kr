---
title: is_placeholder 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- functional/std::is_placeholder
dev_langs:
- C++
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1dd65d50dd2a4b42b949c7ce649c2dcca71f4d72
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
---
# <a name="isplaceholder-class"></a>is_placeholder 클래스

형식이 자리 표시자인지 테스트합니다.

## <a name="syntax"></a>구문

구조체 is_placeholder {static const int 값;을 (를);

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

## <a name="requirements"></a>요구 사항

**헤더:** \<functional>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[_1 개체](../standard-library/1-object.md)<br/>
