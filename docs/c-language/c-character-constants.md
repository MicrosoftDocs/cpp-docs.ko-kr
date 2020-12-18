---
description: '자세한 정보: C 문자 상수'
title: C 문자 상수
ms.date: 11/04/2016
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
ms.openlocfilehash: 2503fc983d79f363f525b22172d2113393b41091
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211559"
---
# <a name="c-character-constants"></a>C 문자 상수

"문자 상수"는 표현 가능한 문자 집합의 단일 문자를 작은따옴표( **' '** )로 묶어 구성합니다. 문자 상수는 [실행 문자 집합](../c-language/execution-character-set.md)에서 문자를 나타내는 데 사용됩니다.

## <a name="syntax"></a>구문

*character-constant*: **'** *c-char-sequence* **'**

**L'** *c-char-sequence* **'**

*c-char-sequence*: *c-char*

*c-char-sequence c-char*

*c-char*: 작은 따옴표( **'** ), 백슬래시( **\\** ) 또는 줄 바꿈 문자를 제외한 소스 문자 집합의 모든 멤버

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

## <a name="see-also"></a>참조

[C 상수](../c-language/c-constants.md)
