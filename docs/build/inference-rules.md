---
title: 유추 규칙
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: cb67fc8fe8e65814c9b169f7936c7d225d26e1e3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471047"
---
# <a name="inference-rules"></a>유추 규칙

유추 규칙 대상을 업데이트 하 고 대상에 대 한 종속 항목을 유추 하는 명령을 제공 합니다. 유추 규칙에 대 한 확장 된 단일 대상 일치 종속 하 고 동일한 기본 이름을 합니다. 유추 규칙은 사용자 정의 또는 미리 정의 된; 미리 정의 된 규칙을 재정의할 수 있습니다.

종속성을 오래 된 명령이 없고 줄에 [입니다. 접미사](../build/dot-directives.md) NMAKE 대상과 기존 일치 규칙을 현재 또는 지정 된 디렉터리에 파일을 사용 하 여 종속 항목의 확장명을 포함 합니다. 둘 이상의 규칙과 기존 파일과 일치 하는 경우는 **합니다. 접미사** 목록 사용 하는 결정; 우선 순위 목록이 왼쪽에서 오른쪽으로 이어집니다. 종속 파일 존재 하지 않는 다른 설명 블록에 나열 되지 않는 경우 유추 규칙 누락 된 종속 파일에서 만들 수 다른 동일한 기본 이름 사용 하 여 합니다. 설명 블록의 대상이 없거나 종속 명령에 대상 유추 규칙을 업데이트할 수 있습니다. 유추 규칙 설명 블록이 없는 경우에 명령줄 대상을 빌드할 수 있습니다. 명시적 종속 파일이 지정 된 경우에 NMAKE 유추 된 종속에 대 한 규칙을 호출할 수 있습니다.

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

[규칙 정의](../build/defining-a-rule.md)

[일괄 처리 모드 규칙](../build/batch-mode-rules.md)

[미리 정의 된 규칙](../build/predefined-rules.md)

[유추 된 종속 파일과 규칙](../build/inferred-dependents-and-rules.md)

[유추 규칙의 우선 순위](../build/precedence-in-inference-rules.md)

## <a name="see-also"></a>참고 항목

[NMAKE 참조](../build/nmake-reference.md)