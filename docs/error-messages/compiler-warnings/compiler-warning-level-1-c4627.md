---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4627'
title: 컴파일러 경고(수준 1) C4627
ms.date: 09/09/2018
f1_keywords:
- C4627
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
ms.openlocfilehash: fc4c6c3931775b090dfd4c7c2fd5fd97441d40d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281446"
---
# <a name="compiler-warning-level-1-c4627"></a>컴파일러 경고(수준 1) C4627

> '*header_file*': 미리 컴파일된 헤더 사용을 찾을 때 건너뛰었습니다.

현재 소스 파일에 [/Yu \( Use 미리 컴파일된 헤더 파일 사용)](../../build/reference/yu-use-precompiled-header-file.md) 옵션이 설정 된 경우 컴파일러는 미리 컴파일된 헤더를 포함 하기 전에 파일의 모든 항목을 무시 합니다. **C4627** 는 미리 컴파일된 헤더 파일 앞에 *header_file* 포함 되어 있고 미리 컴파일된 헤더에 *header_file* 도 포함 되지 않은 경우 Visual Studio 2015 이전 버전에서 생성 됩니다.

## <a name="example"></a>예제

이 샘플은 오류가 발생 하는 방법을 보여 주고 문제를 해결 하는 방법을 보여 줍니다.

```cpp
// c4627.cpp
#include <iostream>       // C4627 - iostream not included by pch.h
#include "pch.h"          // precompiled header file that does not include iostream
// #include <iostream>    // To fix, move the iostream header include here from above
int main()
{
    std::cout << "std::cout is defined!\n";
}
```

## <a name="see-also"></a>참고 항목

[미리 컴파일된 헤더 파일 만들기](../../build/creating-precompiled-header-files.md)
