---
title: 버퍼링 효과
ms.date: 11/04/2016
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
ms.openlocfilehash: e10b28edffdfe3411f86c031bfd12ea886410e20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413790"
---
# <a name="effects-of-buffering"></a>버퍼링 효과

다음 예제에서는 버퍼링 효과 보여 줍니다. 프로그램에서 `please wait`를 인쇄하고 5초 기다린 후 계속하도록 할 수 있습니다. 그러나 출력이 버퍼링되기 때문에 반드시 이런 방식으로 작동하지는 않습니다.

```cpp
// effects_buffering.cpp
// compile with: /EHsc
#include <iostream>
#include <time.h>
using namespace std;

int main( )
{
   time_t tm = time( NULL ) + 5;
   cout << "Please wait...";
   while ( time( NULL ) < tm )
      ;
   cout << "\nAll done" << endl;
}
```

프로그램이 논리적으로 작동하도록 하려면 메시지가 표시될 때 `cout` 개체 자체가 비어 있어야 합니다. `ostream` 개체를 플러시하려면 `flush` 조작자로 보냅니다.

```cpp
cout <<"Please wait..." <<flush;
```

이 단계에서는 버퍼를 플러시하여 메시지가 인쇄된 후 대기하도록 합니다. 사용할 수도 있습니다는 `endl` 조작자를 사용할 수 있습니다 또는 버퍼를 플러시하고 캐리지 리턴-줄 바꿈, 출력을 `cin` 개체. 이 개체는 `cerr` 또는 `clog` 개체와 함께 일반적으로 `cout` 개체에 연결됩니다. 따라서 `cin` , `cerr` 또는 `clog` 개체를 사용하면 `cout` 개체가 플러시됩니다.

## <a name="see-also"></a>참고자료

[출력 스트림](../standard-library/output-streams.md)<br/>
