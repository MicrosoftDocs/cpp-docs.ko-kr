---
title: 전처리기 문법 요약(C/C++)
description: Microsoft C/c + + 컴파일러 (MSVC) 전처리기 문법 구문을 정의 하 고 설명 합니다.
ms.date: 01/22/2021
helpviewer_keywords:
- grammar
- preprocessor, grammar
ms.openlocfilehash: dbe46a67337bf55cb98100878dedb8c92120472b
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713638"
---
# <a name="preprocessor-grammar-summary-cc"></a>전처리기 문법 요약(C/C++)

이 문서에서는 C 및 c + + 전처리기의 공식 문법을 설명 합니다. 전처리 지시문 및 연산자의 구문에 대해 설명 합니다. 자세한 내용은 [전처리기](../preprocessor/preprocessor.md) 및 [Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)를 참조 하세요.

## <a name="definitions-for-the-grammar-summary"></a><a name="definitions"></a> 문법 요약에 대 한 정의

구문 정의에서 단말은 엔드포인트입니다. 다른 확인은 가능하지 않습니다. 단말에는 예약어와 사용자 정의 식별자의 집합이 포함됩니다.

비단말은 구문에서 자리 표시자입니다. 대부분 이 구문 요약의 다른 곳에서 정의되어 있습니다. 정의는 재귀적일 수 있습니다. 다음 비 터미널은 *c + + 언어 참조* 의 [어휘 규칙](../cpp/lexical-conventions.md) 섹션에서 정의 됩니다.

*`constant`*, *`constant-expression`*, *`identifier`*, *`keyword`*, *`operator`*, *`punctuator`*

선택적 구성 요소는 첨자 <sub>opt</sub>로 나타냅니다. 예를 들어 다음 구문은 중괄호로 묶인 선택적 식을 나타냅니다.

**`{`***`expression`* <sub>opt</sub>**`}`**

## <a name="document-conventions"></a><a name="conventions"></a> 문서 규칙

규칙은 구문의 여러 구성 요소에 대해 여러 글꼴 특성을 사용합니다. 기호 및 글꼴은 다음과 같습니다.

| 특성 | 설명 |
|---------------|-----------------|
| *`nonterminal`* | 기울임꼴은 비터미널을 나타냅니다. |
| **`#include`** | 굵게 표시된 터미널은 다음과 같이 입력해야 할 리터럴 예약어 및 기호입니다. 이 컨텍스트의 문자는 항상 대/소문자를 구분합니다. |
| <sub>opt</sub> | 뒤에 <sub>opt</sub>가 오는 비터미널은 항상 선택 사항입니다.|
| default typeface | 이 서체에서 설명하거나 나열된 집합의 문자를 C 문의 터미널로 사용될 수 있습니다. |

**`:`** 비터미널 뒤에 오는 콜론 ()은 해당 정의를 소개 합니다. 다른 정의는 별도의 줄에 나열됩니다.

코드 구문 블록에서 기본 서체의 이러한 기호는 특별 한 의미가 있습니다.

| 기호 | 설명 |
|---|---|
| \[ ] | 대괄호는 선택적 요소를 둘러쌉니다. |
| { \| } | 세로 막대로 구분 된 중괄호 (...)입니다. |
| ... | 이전 요소 패턴을 반복할 수 있음을 나타냅니다. |

코드 구문 블록에서 쉼표 ( `,` ), 마침표 ( `.` ), 세미 콜론 ( `;` ), 콜론 (), `:` 괄호 (), 큰따옴표 () `( )` `"` 및 작은따옴표 ( `'` )는 리터럴입니다.

## <a name="preprocessor-grammar"></a><a name="grammar"></a> 전처리기 문법

*`control-line`*:\
&emsp;**`#define`***`identifier`* *`token-string`* <sub>opt</sub>\
&emsp;**`#define`***`identifier`* **`(`** *`identifier`* <sub>opt</sub> **`,`** ... **`,`** *`identifier`* <sub></sub> **`)`** opt *`token-string`* <sub>opt</sub>\
&emsp;**`#include`** **`"`**_`path-spec`_**`"`**\
&emsp;**`#include`** **`<`**_`path-spec`_**`>`**\
&emsp;**`#line`***`digit-sequence`* **`"`**_`filename`_**`"`** <sub>opt</sub>\
&emsp;**`#undef`** *`identifier`*\
&emsp;**`#error`** *`token-string`*\
&emsp;**`#pragma`** *`token-string`*

*`constant-expression`*:\
&emsp;**`defined(`** *`identifier`* **`)`**\
&emsp;**`defined`** *`identifier`*\
&emsp;기타 상수 식

*`conditional`*:\
&emsp; *`if-part`* *`elif-parts`* <sub>opt</sub> *`else-part`* <sub>opt</sub> *`endif-line`*

*`if-part`*:\
&emsp;*`if-line`* *`text`*

*`if-line`*:\
&emsp;**`#if`** *`constant-expression`*\
&emsp;**`#ifdef`** *`identifier`*\
&emsp;**`#ifndef`** *`identifier`*

*`elif-parts`*:\
&emsp;*`elif-line`* *`text`*\
&emsp;*`elif-parts`* *`elif-line`* *`text`*

*`elif-line`*:\
&emsp;**`#elif`** *`constant-expression`*

*`else-part`*:\
&emsp;*`else-line`* *`text`*

*`else-line`*:\
&emsp;**`#else`**

*`endif-line`*:\
&emsp;**`#endif`**

*`digit-sequence`*:\
&emsp;*`digit`*\
&emsp;*`digit-sequence`* *`digit`*

*`digit`* : one of\
&emsp;**`0` `1` `2` `3` `4` `5` `6` `7` `8` `9`**

*`token-string`*:\
&emsp;문자열 *`token`*

*`token`*:\
&emsp;*`keyword`*\
&emsp;*`identifier`*\
&emsp;*`constant`*\
&emsp;*`operator`*\
&emsp;*`punctuator`*

*`filename`*:\
&emsp;올바른 운영 체제 파일 이름

*`path-spec`*:\
&emsp;Legal file path

*`text`*:\
&emsp;임의의 텍스트 시퀀스

> [!NOTE]
> *C + + 언어 참조* 의 [어휘 규칙](../cpp/lexical-conventions.md) 섹션인 *`constant`* ,,,, *`constant-expression`* *`identifier`* *`keyword`* *`operator`* 및 *`punctuator`* 에서는 다음과 같은 비 터미널이 확장 됩니다.

## <a name="see-also"></a>참고 항목

[C/C++ 전처리기 참조](../preprocessor/c-cpp-preprocessor-reference.md)
