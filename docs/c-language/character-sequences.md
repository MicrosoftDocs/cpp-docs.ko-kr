---
description: '자세한 정보: 문자 시퀀스'
title: 문자 시퀀스
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: ac5642371389047bd8ce3a83e02dc13802167dc0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305080"
---
# <a name="character-sequences"></a>문자 시퀀스

**ANSI 3.8.2** 소스 파일 문자 시퀀스의 매핑

전처리기 문은 이스케이프 시퀀스가 지원되지 않는 경우를 제외하고 소스 파일 문과 같은 문자 설정을 사용합니다.

따라서 include 파일에 대한 경로를 지정하려면 백슬래시를 하나만 사용해야 합니다.

```
#include "path1\path2\myfile"
```

소스 코드 내에서는 두 개의 백슬래시가 필요합니다.

```
fil = fopen( "path1\\path2\\myfile", "rt" );
```

## <a name="see-also"></a>참조

[전처리 지시문](../c-language/preprocessing-directives.md)
