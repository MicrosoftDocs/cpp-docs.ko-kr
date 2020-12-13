---
description: 메이크파일 전처리 지시문에 대해 자세히 알아보세요.
title: 메이크파일 전처리 지시문
ms.date: 08/11/2019
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
ms.openlocfilehash: 7c394e3547044be661fea5a8ec86f05a3b93e967
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138074"
---
# <a name="makefile-preprocessing-directives"></a>메이크파일 전처리 지시문

전처리 지시문은 대/소문자를 구분 하지 않습니다. 초기 느낌표 (!)는 줄의 시작 부분에 표시 되어야 합니다. 0 개 이상의 공백이 나 탭은 느낌표에 대해 느낌표 뒤에 올 수 있습니다.

- `!CMDSWITCHES` { `+` &#124; `-` }*옵션* ...

   각 *옵션* 을 on 또는 off로 설정 합니다. 공백 또는 탭은 or 연산자 앞에 나와야 합니다 `+` `-` . 연산자와 [옵션 문자](running-nmake.md#nmake-options)사이에는 아무것도 표시 되지 않습니다. 문자는 대/소문자를 구분 하지 않으며 슬래시 () 없이 지정 됩니다 `/` . 일부 옵션을 설정 하 고 다른 옵션을 해제 하려면의 별도 사양을 사용 `!CMDSWITCHES` 합니다.

   메이크파일에는/D,/I,/N 및/S만 사용할 수 있습니다. Tools.ini/F,/HELP,/NOLOGO,/X 및/?를 제외한 모든 옵션을 사용할 수 있습니다. 설명 블록에 지정 된 변경 내용은 다음 설명 블록까지 적용 되지 않습니다. 이 지시문은 **Makeflags** 를 업데이트 합니다. **Makeflags** 가 지정 된 경우 재귀 중에 변경 내용이 상속 됩니다.

- `!ERROR`*텍스트*

   U1050에 *텍스트* 를 표시 한 다음,/K,/i, `.IGNORE` , `!CMDSWITCHES` 또는 대시 () 명령 한정자를 사용 하는 경우에도 NMAKE를 중단 `-` 합니다. *텍스트* 앞의 공백이 나 탭은 무시 됩니다.

- `!MESSAGE`*텍스트*

   *텍스트* 를 표준 출력으로 표시 합니다. *텍스트* 앞의 공백이 나 탭은 무시 됩니다.

- `!INCLUDE` [ `<` ] *filename* [ `>` ]

   *파일 이름을* 메이크파일로 읽은 다음 현재 메이크파일을 계속 합니다. NMAKE는 지정 된 또는 현재 디렉터리에서 먼저 *파일 이름을* 검색 한 다음 부모 메이크파일의 디렉터리를 재귀적으로 검색 한 다음 include 매크로로 지정 된 디렉터리에서 *filename* 이 꺾쇠 괄호 ()로 묶여 있는 경우 `< >` 처음에 include 환경 변수로 설정 됩니다.  `.SUFFIXES`설정, `.PRECIOUS` 및 유추 규칙을 재귀적 메이크파일에 전달 하는 데 유용 합니다.

- `!IF`*constant_expression*

   `!IF`는와 next 사이에서 문을 처리 하 고, `!ELSE` `!ENDIF` *constant_expression* 0이 아닌 값으로 계산 되는 경우를 처리 합니다.

- `!IFDEF` *매크로 이름*

   `!IFDEF`와 다음 사이 `!ELSE` 또는 `!ENDIF` *macroname* 이 정의 된 경우 문을 처리 합니다. Null 매크로가 정의 된 것으로 간주 됩니다.

- `!IFNDEF` *매크로 이름*

   `!IFNDEF`와 다음 사이의 문이나 `!ELSE` `!ENDIF` *macroname* 이 정의 되지 않은 경우를 처리 합니다.

- `!ELSE` [ `IF` *constant_expression* &#124; `IFDEF` *macroname* &#124; `IFNDEF` *macroname*]

   `!ELSE` `!ENDIF` 이전 `!IF` , `!IFDEF` 또는 `!IFNDEF` 문이 0으로 계산 되는 경우와 다음 사이의 문을 처리 합니다. 선택적 키워드를 통해 전처리를 추가로 제어할 수도 있습니다.

- `!ELSEIF`

   `!ELSE IF`의 동의어입니다.

- `!ELSEIFDEF`

   `!ELSE IFDEF`의 동의어입니다.

- `!ELSEIFNDEF`

   `!ELSE IFNDEF`의 동의어입니다.

- `!ENDIF`

   , 또는 블록의 끝을 표시 `!IF` `!IFDEF` `!IFNDEF` 합니다. `!ENDIF`같은 줄의 뒤에 오는 모든 텍스트는 무시 됩니다.

- `!UNDEF` *매크로 이름*

   를 *해제* 합니다.

## <a name="see-also"></a>참고 항목

- [메이크파일 전처리](makefile-preprocessing.md)
