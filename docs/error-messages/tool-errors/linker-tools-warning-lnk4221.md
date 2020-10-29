---
title: 링커 도구 경고 LNK4221
ms.date: 08/19/2019
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: f18224150232384adbf8ee7cc31af7bb7678eae5
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919204"
---
# <a name="linker-tools-warning-lnk4221"></a>링커 도구 경고 LNK4221

이 개체 파일은 이전에 정의 되지 않은 공용 기호를 정의 하지 않으므로이 라이브러리를 사용 하는 모든 링크 작업에서 사용 되지 않습니다.

다음 두 코드 조각을 고려 하십시오.

```cpp
// a.cpp
#include <atlbase.h>
```

```cpp
// b.cpp
#include <atlbase.h>
int function()
{
   return 0;
}
```

파일을 컴파일하고 두 개의 개체 파일을 만들려면 명령 프롬프트에서 **cl/c a. .cpp** .cpp를 실행 합니다. /Lib를 실행 하 여 개체 파일을 연결 하는 경우 **에** 는 LNK4221 경고를 받게 됩니다. **/Lib (/lib) 링크** 를 실행 하 여 개체를 연결 하는 경우에는 경고가 표시 되지 않습니다.

링커는 LIFO (LIFO) 방식으로 작동 하기 때문에 두 번째 시나리오에서는 경고가 발생 하지 않습니다. 첫 번째 시나리오에서는 .obj 이전에는 b. .obj를 처리 하 고,에는 추가할 새 기호가 없습니다. 링커가 .obj를 먼저 처리 하도록 지시 하면 경고를 방지할 수 있습니다.

::: moniker range=">=msvc-160"

이 오류의 일반적인 원인은 두 소스 파일이 **미리 컴파일된 헤더** 필드에 지정 된 것과 동일한 헤더 파일 이름을 사용 하 여 [/Yc (미리 컴파일된 헤더 파일 만들기)](../../build/reference/yc-create-precompiled-header-file.md) 옵션을 지정 하는 경우입니다. 기본적 *으로 .pch는 .pch를 포함 하* 고 새 기호를 추가 하지 않으므로이 문제의 일반적인 원인은 *.pch* 를 *처리 하는* 것입니다. 다른 소스 파일에 **/yc** 가 포함 된 *.pch. h* 가 포함 되어 있고 연결 된 .obj 파일이 pch. .obj 이전에 처리 되는 경우 링커에서는 LNK4221을 throw 합니다.

::: moniker-end

::: moniker range="<=msvc-150"

이 오류의 일반적인 원인은 두 소스 파일이 **미리 컴파일된 헤더** 필드에 지정 된 것과 동일한 헤더 파일 이름을 사용 하 여 [/Yc (미리 컴파일된 헤더 파일 만들기)](../../build/reference/yc-create-precompiled-header-file.md) 옵션을 지정 하는 경우입니다. 기본적 *으로 stdafx.h는 stdafx.h를 포함 하* *고 새* 기호를 추가 하지 않으므로 *stdafx.h* 를 사용 하는 것이 문제의 일반적인 원인입니다. 다른 소스 파일에 **/yc** 가 있는 *stdafx.h* 가 포함 되어 있고 관련 .obj 파일이 stdafx.h 이전에 처리 되는 경우 링커는 LNK4221을 throw 합니다.

::: moniker-end

이 문제를 해결 하는 한 가지 방법은 미리 컴파일된 각 헤더에 대해 **/yc** 를 사용 하 여 소스 파일이 하나만 포함 되어 있는지 확인 하는 것입니다. 다른 모든 소스 파일은 미리 컴파일된 헤더를 사용 해야 합니다. 이 설정을 변경 하는 방법에 대 한 자세한 내용은 [/yu (미리 컴파일된 헤더 파일 사용)](../../build/reference/yu-use-precompiled-header-file.md)를 참조 하세요.
