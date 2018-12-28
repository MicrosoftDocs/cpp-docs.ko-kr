﻿---
title: 와일드카드 식
ms.date: 11/04/2016
f1_keywords:
- _setargv
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
ms.openlocfilehash: 2d495f94f2e3fb7b88d235edc7b98f8e90775393
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507435"
---
# <a name="wildcard-expansion"></a>와일드카드 식

## <a name="microsoft-specific"></a>Microsoft 전용

명령줄에서 파일 이름과 경로 인수를 지정하기 위해 와일드카드, 즉 물음표(?)와 별표(*)를 사용할 수 있습니다.

명령줄 인수는 `argv` 문자열 배열에서 기본적으로 별도의 문자열로 와일드카드를 확장하지 않는 `_setargv`(와이드 문자 환경에서는 `_wsetargv`)라는 루틴에 의해 처리됩니다. 와일드카드 확장 사용에 대한 자세한 내용은 [와일드카드 인수 확장](../c-language/expanding-wildcard-arguments.md)을 참조하십시오.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고

[main: 프로그램 시작](../cpp/main-program-startup.md)
