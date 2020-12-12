---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4702'
title: 컴파일러 경고(수준 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: 9a171641a2c923083471d510e27fbdb3ebd08832
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133798"
---
# <a name="compiler-warning-level-4-c4702"></a>컴파일러 경고(수준 4) C4702

접근할 수 없는 코드

이 경고는 Visual Studio .NET 2003: 접근할 수 없는 코드에 대해 수행 된 컴파일러 규칙 작업의 결과입니다. 컴파일러 (백 엔드)에서 접근할 수 없는 코드를 검색 하면 수준 4 경고 C4702 생성 됩니다.

Visual C++ Visual Studio .NET 2003 및 Visual Studio .NET 버전 둘 다에서 유효한 코드의 경우 접근할 수 없는 코드를 제거 하거나 일부 실행 흐름에서 모든 소스 코드를 연결할 수 있도록 보장 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 C4702를 생성 합니다.

```cpp
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

**/Gx**, **/EHc**, **/ehsc** 또는 **/EHac** 를 사용 하 여 컴파일하고 extern C 함수를 사용 하는 경우 extern c 함수는 throw 되지 않는 것으로 간주 되기 때문에 코드에 연결할 수 없게 되므로 catch 블록에 연결할 수 없습니다.  함수가 throw 될 수 있으므로이 경고가 유효 하지 않은 경우 throw 되는 예외에 따라 **/eha** 또는 **/EHs** 를 사용 하 여 컴파일합니다.

자세한 내용은 [/Ceh (예외 처리 모델)](../../build/reference/eh-exception-handling-model.md) 를 참조 하세요.

다음 샘플에서는 C4702를 생성 합니다.

```cpp
// C4702b.cpp
// compile with: /W4 /EHsc
#include <iostream>

using namespace std;
extern "C" __declspec(dllexport) void Function2(){}

int main() {
   try {
      Function2();
   }
   catch (...) {
      cout << "Exp: Function2!" << endl;   // C4702
   }
}
```
