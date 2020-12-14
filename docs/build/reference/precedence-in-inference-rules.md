---
description: '자세히 알아보기: 유추 규칙의 우선 순위'
title: 유추 규칙의 우선 순위
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: b56d01cce63aaaac92e011630e45bcf43e7fe0b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225910"
---
# <a name="precedence-in-inference-rules"></a>유추 규칙의 우선 순위

유추 규칙이 곱하기로 정의 된 경우 NMAKE는 우선 순위가 가장 높은 정의를 사용 합니다. 다음 목록에서는 최고에서 최저 순으로 우선 순위를 보여 줍니다.

1. 메이크파일에 정의 된 유추 규칙 이후 정의는 우선 순위를 갖습니다.

1. Tools.ini에 정의 된 유추 규칙 이후 정의는 우선 순위를 갖습니다.

1. 미리 정의 된 유추 규칙입니다.

## <a name="see-also"></a>참고 항목

[유추 규칙](inference-rules.md)
