---
description: '자세한 정보: C 문자열 리터럴'
title: C 문자열 리터럴
ms.date: 08/31/2018
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
ms.openlocfilehash: c18a13dcc44203399aa6518f53031d29b00a5a4c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207087"
---
# <a name="c-string-literals"></a>C 문자열 리터럴

"문자열 리터럴"은 큰따옴표( **" "** )로 묶은 소스 문자 집합의 문자 시퀀스입니다. 문자열 리터럴은 함께 사용될 경우 null로 끝나는 문자열을 형성하는 문자 시퀀스를 나타냅니다. 항상 와이드 문자열 리터럴의 접두어로 **L** 문자를 사용해야 합니다.

## <a name="syntax"></a>구문

*string-literal*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **"** *s-char-sequence*<sub>opt</sub> **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L"** *s-char-sequence*<sub>opt</sub> **"**

*s-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*

&nbsp;&nbsp;&nbsp;&nbsp;*s-char-sequence* *s-char*

*s-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;큰따옴표("), 백슬래시(\\) 또는 줄 바꿈 문자를 제외한 소스 문자 집합의 모든 멤버

&nbsp;&nbsp;&nbsp;&nbsp;*escape-sequence*

## <a name="remarks"></a>설명

아래 예제는 단순 문자열 리터럴입니다.

```C
char *amessage = "This is a string literal.";
```

[이스케이프 시퀀스](../c-language/escape-sequences.md) 표에 나열된 모든 이스케이프 코드가 문자열 리터럴에서 유효합니다. 문자열 리터럴에서 큰따옴표를 표시하려면 **\\"** 이스케이프 시퀀스를 사용합니다. 작은따옴표( **'** )는 이스케이프 시퀀스 없이 나타낼 수 있습니다. 백슬래시( **\\** )는 문자열 내에 표시될 때 다른 하나의 백슬래시( **\\\\** )와 함께 표시되어야 합니다. 백슬래시가 줄 끝에 있으면 항상 줄 연속 문자로 해석됩니다.

## <a name="see-also"></a>참조

[C 요소](../c-language/elements-of-c.md)
