---
title: 함수 패밀리 개요
description: 제품군 별 Microsoft C 런타임 함수에 대 한 개요입니다.
ms.date: 10/05/2020
ms.assetid: b05a2755-9d11-4ea9-ab97-d00a4e872e16
ms.openlocfilehash: de5192cd03c3821afc646241d75a3e8c6c8c12e3
ms.sourcegitcommit: 8caaf5e00aeb727741a273aecafa15de293426cf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91806515"
---
# <a name="function-family-overview"></a>함수 패밀리 개요

이 섹션에는 함수 패밀리의 C 런타임 라이브러리 루틴이 나열 됩니다.

## <a name="crt-library-routine-families"></a>CRT 라이브러리 루틴 패밀리

[_exec, _wexec](exec-wexec-functions.md)\
새 프로세스를 로드 하 고 실행 하는 함수입니다.

[파일 이름 검색 함수](filename-search-functions.md)\
지정 된 파일 이름을 검색 하 고 검색을 종결 하는 함수입니다.

[및에 대 한 형식 사양 구문 `printf``wprintf`](format-specification-syntax-printf-and-wprintf-functions.md)\
및에 대 한 형식 문자열 및 인수를 설명 합니다 `printf` `wprintf` .

[형식 사양 필드 문자: `scanf` 및 `wscanf`](format-specification-fields-scanf-and-wscanf-functions.md)\
전체 함수 패밀리에 대 한 입력 스트림을 구문 분석 하기 위한 형식 사양 필드에 대해 설명 합니다 `scanf` .

[`is`, `isw` 함수](is-isw-routines.md)\
대문자, ASCII, 숫자, 문장 부호 등의 문자를 테스트 하는 함수입니다.

[`_ismbb` 역함수](ismbb-routines.md)\
알파 문자, 공백 문자, 인쇄 문자 등을 나타내는지 여부에 대 한 정수 값을 테스트 하기 위한 함수입니다.

[`_ismbc` 역함수](ismbc-routines.md)\
멀티 바이트 문자를 테스트 하는 함수입니다 .이 문자는 영숫자, 공백 문자, 인쇄 문자 등을 나타내는지 여부를 나타냅니다.

[연산자 `delete` (CRT)](delete-operator-crt.md)\
Visual Studio 2013부터 유니버설 C 런타임 (CRT)은 c + + 관련 operator delete 함수를 더 이상 지원 하지 않습니다. 이제 c + + 표준 라이브러리의 일부입니다.

[연산자 `new` (CRT)](new-operator-crt.md)\
Visual Studio 2013부터 유니버설 C 런타임 (CRT)은 c + + 관련 operator new 함수를 더 이상 지원 하지 않습니다. 이제 c + + 표준 라이브러리의 일부입니다.

[`printf` 위치 매개 변수 함수](printf-p-positional-parameters.md)\
위치 매개 변수는 형식 문자열의 필드로 대체 되는 인수를 숫자로 지정 합니다.

[`scanf` 형식 필드 문자](scanf-type-field-characters.md)\
형식 문자는와 같은 보안 버전을 비롯 하 여 관련 인수가 함수 패밀리의 문자, 문자열 또는 숫자로 해석 되는지 여부를 결정 합니다 `scanf` `scanf_s` .

[`scanf` 너비 사양](scanf-width-specification.md)\
너비 필드는 해당 필드에 대해 읽을 최대 문자 수를 제어 하는 양의 10 진수 정수입니다. 는 `scanf` 와 같은 보안 버전을 비롯 한 모든 함수 패밀리에 적용 됩니다 `scanf_s` .

[_spawn, _wspawn 함수](spawn-wspawn-functions.md)\
새 프로세스를 만들고 실행 하는 함수입니다.

[`strcoll` 역함수](strcoll-functions.md)\
`strcoll`및 `wcscoll` 함수는 `LC_COLLATE` 로캘 코드 페이지의 범주 설정에 따라 두 문자열을 비교 합니다.

[문자열-숫자 값 함수](string-to-numeric-value-functions.md)\
`strtod`함수 패밀리는 null로 끝나는 문자열을 숫자 값으로 변환 합니다.

[`vprintf` 역함수](vprintf-functions.md)\
`vprintf`함수는 인수 목록에 대 한 포인터를 사용 하 여 서식을 지정 하 고 결과를 지정 된 대상에 씁니다. 함수는 수행 되는 매개 변수 유효성 검사, 와이드 문자열 또는 싱글바이트 문자열 사용 여부, 출력 대상 및 형식 문자열에서 매개 변수가 사용 되는 순서를 지정 하는 지원에 따라 달라 집니다.

## <a name="see-also"></a>참고 항목

[C 런타임 라이브러리 참조](c-run-time-library-reference.md)