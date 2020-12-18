---
description: '자세한 정보: C 주석'
title: C 주석
ms.date: 06/25/2018
helpviewer_keywords:
- code comments, C code
- comments, documenting code
- comments, C code
- /* */ comment delimiters
- comments
ms.assetid: 0f5f2825-e673-49e7-8669-94e2f5294989
ms.openlocfilehash: 64ce3dea188e75545953b3427cd508dac5420a83
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284578"
---
# <a name="c-comments"></a>C 주석

"주석"은 정방향 슬래시/별표 조합(<strong>/\*</strong>)으로 시작하는 문자 시퀀스로, 컴파일러에 의해 단일 공백 문자로 처리되거나 무시됩니다. 주석은 줄 바꿈 문자를 비롯하여 표현 가능한 문자 집합의 모든 문자 조합을 포함할 수 있습니다. 단, "종료 주석" 구분 기호(<strong>\*/</strong>)는 제외됩니다. 주석은 두 줄 이상을 차지할 수 있지만 중첩될 수는 없습니다.

주석은 공백 문자가 허용되는 어느 곳에든 나타날 수 있습니다. 컴파일러는 주석을 단일 공백 문자로 처리하므로 토큰 내에 주석을 포함시킬 수 없습니다. 컴파일러는 주석의 문자를 무시합니다.

주석을 사용하여 코드를 문서화할 수 있습니다. 다음 예제는 컴파일러에서 허용되는 주석입니다.

```C
/* Comments can contain keywords such as
   for and while without generating errors. */
```

주석은 코드 문과 같은 줄에 표시될 수 있습니다.

```C
printf( "Hello\n" );  /* Comments can go here */
```

설명용 주석 블록이 함수 또는 프로그램 모듈 앞에 오도록 선택할 수 있습니다.

```C
/* MATHERR.C illustrates writing an error routine
* for math functions.
*/
```

주석에는 중첩된 주석이 포함될 수 없으므로 다음 예제에서는 오류가 발생합니다.

```C
/* Comment out this routine for testing

   /* Open file */
    fh = _open( "myfile.c", _O_RDONLY );
    .
    .
    .
*/
```

이 오류는 컴파일러가 `*/`이라는 단어 뒤의 첫 번째 `Open file`를 주석의 끝으로 인식하기 때문에 발생합니다. 컴파일러는 주석이 끝난 다음에 오는 나머지 텍스트를 처리하려 하기 때문에 주석 밖에서 `*/`을 발견할 경우 오류를 표시합니다.

테스트 목적으로 비활성화된 어떤 코드 줄을 렌더링하기 위해 주석을 사용하는 경우, 프로세서는 `#if` 및 `#endif`를 지시하며 이 작업에 조건부 컴파일을 사용하는 것도 또 다른 유용한 방법입니다. 자세한 내용은 *전처리기 참조* 의 [전처리기 지시문](../preprocessor/preprocessor-directives.md)을 참조하세요.

**Microsoft 전용**

또한 Microsoft 컴파일러에서는 두 개의 슬래시( __//__ )가 앞에 오는 한 줄 주석이 지원됩니다. /Za(ANSI 표준)로 컴파일할 경우 이러한 주석은 오류를 발생시킵니다. 이 주석은 두 번째 줄로 확장될 수 없습니다.

```C
// This is a valid comment
```

두 개의 슬래시( __//__ )로 시작하는 주석은 이스케이프 문자가 앞에 나오지 않는 다음 줄 바꿈 문자로 종료됩니다. 다음 예제에서는 줄 바꿈 문자가 백슬래시( **\\** ) 뒤에 와서 "이스케이프 시퀀스"를 만듭니다. 이 이스케이프 시퀀스는 컴파일러가 다음 줄을 앞 줄의 일부로 취급하게 합니다. 자세한 내용은 [이스케이프 시퀀스](../c-language/escape-sequences.md)를 참조하세요.

```C
// my comment \
    i++;
```

따라서 `i++;` 문은 주석 처리됩니다.

기본적으로 Microsoft C에는 Microsoft 확장을 사용하도록 설정되어 있습니다. /Za를 사용하여 이러한 확장을 사용하지 않도록 설정합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[C 토큰](../c-language/c-tokens.md)
