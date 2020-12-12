---
description: '자세히 알아보기: 유추 규칙'
title: 유추 규칙
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: fc063f71ff88442ce6f7fc02c5b22f015ce0010c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199755"
---
# <a name="inference-rules"></a>유추 규칙

유추 규칙은 대상을 업데이트 하 고 대상에 대 한 종속 항목을 유추 하는 명령을 제공 합니다. 유추 규칙의 확장 프로그램은 기본 이름이 동일한 단일 대상과 종속 항목을 찾습니다. 유추 규칙은 사용자 정의 또는 미리 정의 된 규칙입니다. 미리 정의 된 규칙을 재정의할 수 있습니다.

오래 된 종속성에 명령이 없고 이면이 고, 그렇지 않으면 [입니다. 접미사](dot-directives.md) 는 종속의 확장을 포함 하 고, NMAKE는 확장명이 대상과 일치 하는 규칙 및 현재 또는 지정 된 디렉터리에 있는 기존 파일을 사용 합니다. 기존 파일과 일치 하는 규칙이 둘 이상인 경우 **입니다. 접미사** 목록에서 사용할 유형을 결정 합니다. 우선 순위 계층이 이어집니다를 왼쪽에서 오른쪽으로 나열 합니다. 종속 파일이 존재 하지 않고 다른 설명 블록의 대상으로 나열 되어 있지 않은 경우 유추 규칙이 동일한 기본 이름을 가진 다른 파일에서 누락 된 종속 파일을 만들 수 있습니다. 설명 블록의 대상에 종속 항목이 나 명령이 없으면 유추 규칙에서 대상을 업데이트할 수 있습니다. 유추 규칙은 설명 블록이 없는 경우에도 명령줄 대상을 빌드할 수 있습니다. NMAKE는 명시적 종속이 지정 된 경우에도 유추 된 종속에 대 한 규칙을 호출할 수 있습니다.

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

[규칙 정의](defining-a-rule.md)

[일괄 처리 모드 규칙](batch-mode-rules.md)

[미리 정의된 규칙](predefined-rules.md)

[유추된 종속 파일과 규칙](inferred-dependents-and-rules.md)

[유추 규칙의 우선 순위](precedence-in-inference-rules.md)

## <a name="see-also"></a>참고 항목

[NMAKE 참조](nmake-reference.md)
