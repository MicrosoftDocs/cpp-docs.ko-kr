---
title: 문자열 리터럴 요약
ms.date: 11/04/2016
ms.assetid: d2693900-f4e2-4820-b7de-085d51827aee
ms.openlocfilehash: 72f5aa6405ae97bfb6141db737affa0c3aca2a65
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648125"
---
# <a name="summary-of-string-literals"></a>문자열 리터럴 요약

*string-literal*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**'** *s-char-sequence*<sub>opt</sub> **'**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L'** *s-char-sequence*sub>opt</sub> **'**

*s-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char-sequence* *s-char*

*s-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;큰따옴표("), 백슬래시(\\) 또는 줄 바꿈 문자를 제외한 소스 문자 집합의 멤버

## <a name="see-also"></a>참고 항목

[어휘 문법](../c-language/lexical-grammar.md)