---
description: '자세한 정보: 매크로 정의의 우선 순위'
title: 매크로 정의의 우선 순위
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 1738c4ba77f330103395278a6daae169b04fae4c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225897"
---
# <a name="precedence-in-macro-definitions"></a>매크로 정의의 우선 순위

매크로에 정의가 여러 개 있는 경우 NMAKE는 우선 순위가 가장 높은 정의를 사용 합니다. 다음 목록에서는 최고에서 최저 순으로 우선 순위를 보여 줍니다.

1. 명령줄에 정의 된 매크로

1. 메이크파일 또는 포함 파일에 정의 된 매크로

1. 상속 된 환경 변수 매크로

1. Tools.ini 파일에 정의 된 매크로

1. [CC](command-macros-and-options-macros.md) 및 [as](command-macros-and-options-macros.md) 와 같은 미리 정의 된 매크로

변수를 사용 하 여 환경 변수에서 상속 된 매크로를 사용 하 여 동일한 이름의 메이크파일 매크로를 재정의 합니다. 사용 **! UNDEF** -명령줄을 재정의 합니다.

## <a name="see-also"></a>참고 항목

[NMAKE 매크로 정의](defining-an-nmake-macro.md)
