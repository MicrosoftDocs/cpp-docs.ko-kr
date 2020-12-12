---
description: Batch-Mode 규칙에 대해 자세히 알아보세요.
title: 일괄 처리 모드 규칙
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 73439082b4e2ad8e33b104329d861ddd1919ec63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182738"
---
# <a name="batch-mode-rules"></a>일괄 처리 모드 규칙

```
{frompath}.fromext{topath}.toext::
   commands
```

N 개 명령이이 유추 규칙을 통과 하는 경우 일괄 처리 모드 유추 규칙은 유추 규칙의 호출을 하나만 제공 합니다. 일괄 처리 모드 유추 규칙이 없으면 N 개의 명령을 호출 해야 합니다. N은 유추 규칙을 트리거하는 종속 항목의 수입니다.

일괄 처리 모드 유추 규칙이 포함 된 메이크파일은 NMAKE 버전 1.62 이상을 사용 해야 합니다. NMAKE 버전을 확인 하려면 NMAKE 버전 1.62 이상을 사용 하 여 _NMAKE_VER 매크로를 실행 합니다. 이 매크로는 Visual C++ 제품 버전을 나타내는 문자열을 반환 합니다.

표준 유추 규칙과의 유일한 구문상 차이점은 일괄 처리 모드 유추 규칙이 이중 콜론 (::)으로 종료 된다는 것입니다.

> [!NOTE]
> 호출 되는 도구는 여러 파일을 처리할 수 있어야 합니다. 일괄 처리 모드 유추 규칙은 `$<` 종속 파일에 액세스 하는 매크로로를 사용 해야 합니다.

일괄 처리 모드 유추 규칙은 빌드 프로세스의 속도를 높일 수 있습니다. 컴파일러 드라이버가 한 번만 호출 되기 때문에 배치에서 컴파일러에 파일을 제공 하는 것이 더 빠릅니다. 예를 들어 C 및 c + + 컴파일러는 프로세스 중에 메모리 상주 상태를 유지할 수 있으므로 파일 집합을 처리할 때 더 나은 성능을 발휘 합니다.

다음 예제에서는 배치 모드 유추 규칙을 사용 하는 방법을 보여 줍니다.

```
#
# sample makefile to illustrate batch-mode inference rules
#
O = .
S = .
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj
CFLAGS = -nologo

all : $(Objs)

!ifdef NOBatch
{$S}.cpp{$O}.obj:
!else
{$S}.cpp{$O}.obj::
!endif
   $(CC) $(CFLAGS) -Fd$O\ -c $<

$(Objs) :

#end of makefile
```

NMAKE는 일괄 처리 모드 유추 규칙 없이 다음과 같은 출력을 생성 합니다.

```
E:\tmp> nmake -f test.mak -a NOBatch=1

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.
        cl -nologo -Fd.\ -c .\foo1.cpp
foo1.cpp
        cl -nologo -Fd.\ -c .\foo2.cpp
foo2.cpp
        cl -nologo -Fd.\ -c .\foo3.cpp
foo3.cpp
        cl -nologo -Fd.\ -c .\foo4.cpp
foo4.cpp
```

NMAKE는 일괄 처리 모드 유추 규칙을 사용 하 여 다음과 같은 결과를 생성 합니다.

```
E:\tmp> nmake -f test.mak -a

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.

        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp
foo1.cpp
foo2.cpp
foo3.cpp
foo4.cpp
Generating Code...
```

## <a name="see-also"></a>참고 항목

[유추 규칙](inference-rules.md)
