---
title: 컴파일러 경고(수준 1) C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: a298eb0c55f96289a0043f3a996b09798745c92d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684224"
---
# <a name="compiler-warning-level-1-c4835"></a>컴파일러 경고(수준 1) C4835

' variable ': 내보낸 데이터의 이니셜라이저는 관리 코드가 호스트 어셈블리에서 먼저 실행 될 때까지 실행 되지 않습니다.

관리 되는 구성 요소 간의 데이터에 액세스 하는 경우에는 네이티브 c + + 가져오기 및 내보내기 메커니즘을 사용 하지 않는 것이 좋습니다. 대신 관리 되는 형식 내에서 데이터 멤버를 선언 하 고 클라이언트에서를 사용 하 여 메타 데이터를 참조 합니다 `#using` . 자세한 내용은 [#using 지시문](../../preprocessor/hash-using-directive-cpp.md)을 참조하세요.

## <a name="examples"></a>예제

다음 샘플에서는 C4835를 생성 합니다.

```cpp
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

다음 샘플에서는 이전 샘플에서 빌드된 구성 요소를 사용 하 여 변수 값이 예상과 다른 것을 보여 줍니다.

```cpp
// C4835_b.cpp
// compile with: /clr C4835.lib
#include <stdio.h>
__declspec(dllimport) int m;
__declspec(dllimport) int *p;

int main() {
   printf("%d\n", m);
   printf("%d\n", p);
}
```

```Output
0
268456008
```
