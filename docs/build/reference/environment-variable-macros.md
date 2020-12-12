---
description: Environment-Variable 매크로에 대 한 자세한 정보
title: 환경 변수 매크로
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
ms.openlocfilehash: b7beaf8f3e98ea7447d798041f7531ed5da671ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192592"
---
# <a name="environment-variable-macros"></a>환경 변수 매크로

NMAKE는 세션이 시작 되기 전에 존재 하는 환경 변수에 대 한 매크로 정의를 상속 합니다. 변수가 운영 체제 환경에서 설정 된 경우 NMAKE 매크로로 사용할 수 있습니다. 상속 된 이름이 대문자로 변환 됩니다. 전처리는 전처리 전에 발생 합니다. /E 옵션을 사용 하면 환경 변수에서 상속 된 매크로가 메이크파일의 동일한 이름을 가진 모든 매크로를 재정의 합니다.

환경 변수 매크로를 세션에서 다시 정의할 수 있으며, 그러면 해당 환경 변수가 변경 됩니다. SET 명령을 사용 하 여 환경 변수를 변경할 수도 있습니다. 그러나 SET 명령을 사용 하 여 세션에서 환경 변수를 변경 해도 해당 매크로는 변경 되지 않습니다.

예를 들어:

```
PATH=$(PATH);\nonesuch

all:
    echo %%PATH%%
```

이 예제에서 변경 내용은 `PATH` 해당 환경 변수를 변경 하 `PATH` 고, `\nonesuch` 경로에 추가 합니다.

환경 변수가 메이크파일의 구문상 잘못 된 문자열로 정의 된 경우 매크로가 생성 되지 않으며 경고가 생성 되지 않습니다. 변수 값에 달러 기호 ($)가 포함 된 경우 NMAKE는 매크로 호출의 시작으로 해석 합니다. 매크로를 사용 하면 예기치 않은 동작이 발생할 수 있습니다.

## <a name="see-also"></a>참고 항목

[특수 NMAKE 매크로](special-nmake-macros.md)
