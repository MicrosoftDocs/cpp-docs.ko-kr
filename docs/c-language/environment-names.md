---
description: '자세한 정보: 환경 이름'
title: 환경 이름
ms.date: 11/04/2016
ms.assetid: 9af409a5-e724-465a-9a21-88d3586c2e92
ms.openlocfilehash: f40da15151385cea4bd581dea8946f50d2b58ea8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213756"
---
# <a name="environment-names"></a>환경 이름

**ANSI 4.10.4.4**[getenv](../c-runtime-library/reference/getenv-wgetenv.md) 함수에 사용되는 환경 목록을 변경하는 메서드 및 환경 이름 집합입니다.

환경 이름 집합에는 제한이 없습니다.

C 프로그램에서 환경 변수를 변경하려면 [_putenv](../c-runtime-library/reference/putenv-wputenv.md) 함수를 호출하세요. Windows 명령줄에서 환경 변수를 변경하려면 SET 명령(예: SET LIB = D:\ LIBS)을 사용하십시오.

운영 체제 명령 셸의 호스트 복사본이 실행 중이어야(CMD.EXE 또는 COMMAND.COM) C 프로그램에서 설정한 환경 변수가 있습니다. 예를 들어, 다음 줄에서

```
system( SET LIB = D:\LIBS );
```

명령 셸(CMD.EXE)의 복사본을 실행하고 환경 변수 LIB를 설정한 후 C 프로그램으로 돌아가 CMD.EXE의 보조 복사본을 종료합니다. CMD.EXE 복사본을 종료하면 임시 환경 변수 LIB가 제거됩니다.

마찬가지로 `_putenv` 함수로 변경한 내용은 프로그램이 끝날 때까지만 지속됩니다.

## <a name="see-also"></a>참조

[라이브러리 함수](../c-language/library-functions.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)
