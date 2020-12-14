---
description: '자세히 알아보기: 유추 된 종속 항목 및 규칙'
title: 유추된 종속 파일과 규칙
ms.date: 11/04/2016
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
ms.openlocfilehash: 9f4c1d14d18c9c693a7bd71f9207ff36aede8e22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191279"
---
# <a name="inferred-dependents-and-rules"></a>유추된 종속 파일과 규칙

NMAKE는 적용 가능한 유추 규칙이 있는 경우 대상에 대해 유추를 유추 한다고 가정 합니다. 규칙은 다음과 같은 경우에 적용 됩니다.

- *toext* 는 대상의 확장과 일치 합니다.

- *fromext* 는 대상의 기본 이름이 있고 현재 또는 지정 된 디렉터리에 있는 파일의 확장과 일치 합니다.

- *fromext* 는에 [있습니다. 접미사](dot-directives.md); 일치 규칙에는 다른 *fromext* 가 더 이상 없습니다 **. 접미사** 우선 순위입니다.

- 명시적인 종속 관계가 없습니다 **. 접미사** 우선 순위입니다.

유추 된 종속 항목으로 인해 예기치 않은 부작용이 발생할 수 있습니다. 대상의 description 블록에 명령이 포함 된 경우 NMAKE는 규칙의 명령 대신 해당 명령을 실행 합니다.

## <a name="see-also"></a>참고 항목

[유추 규칙](inference-rules.md)
