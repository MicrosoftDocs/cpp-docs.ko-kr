---
title: C 문자 상수
ms.date: 11/04/2016
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
ms.openlocfilehash: 5d87b57726f741cc96f2180de33cae01403786ec
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152770"
---
# <a name="c-character-constants"></a>C 문자 상수

"문자 상수"는 표현 가능한 문자 집합의 단일 문자를 작은따옴표(**' '**)로 묶어 구성합니다. 문자 상수는 [실행 문자 집합](../c-language/execution-character-set.md)에서 문자를 나타내는 데 사용됩니다.

## <a name="syntax"></a>구문

*character-constant*: **'** *c-char-sequence* **'**

**L'** *c-char-sequence* **'**

*c-char-sequence*: *c-char*

*c-char-sequence c-char*

*c-char*: 작은 따옴표(**'**), 백슬래시(**\\**) 또는 줄 바꿈 문자를 제외한 소스 문자 집합의 모든 멤버

*escape-sequence*

*escape-sequence*: *simple-escape-sequence*

*octal-escape-sequence*

*hexadecimal-escape-sequence*

*simple-escape-sequence*: 다음 중 하나: **\a \b \f \n \r \t \v**

**\\' \\" \\\ \\?**

*octal-escape-sequence*: **\\**  *octal-digit*

**\\**  *octal-digit octal-digit*

**\\**  *octal-digit octal-digit octal-digit*

*hexadecimal-escape-sequence*: **\x**  *hexadecimal-digit*

*hexadecimal-escape-sequence hexadecimal-digit*

## <a name="see-also"></a>참고 항목

[C 상수](../c-language/c-constants.md)
