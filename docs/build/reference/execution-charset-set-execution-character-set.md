---
description: 다음에 대 한 자세한 정보:/execution-charset (실행 문자 집합 설정)
title: /sv-ecin 문자 집합 (실행 문자 집합 설정)
ms.date: 02/06/2019
f1_keywords:
- execution-charset
- /execution-charset
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
ms.openlocfilehash: 38d17ba1d7e73fa337c81cc0c54f0053bfcff2ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200821"
---
# <a name="execution-charset-set-execution-character-set"></a>/sv-ecin 문자 집합 (실행 문자 집합 설정)

실행 파일에 대 한 실행 문자 집합을 지정할 수 있습니다.

## <a name="syntax"></a>구문

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>인수

*IANA_name*<br/>
IANA에서 정의한 문자 집합 이름입니다.

*CPID*<br/>
코드 페이지 식별자입니다.

## <a name="remarks"></a>설명

**/Execution-charset** 옵션을 사용 하 여 실행 문자 집합을 지정할 수 있습니다. 실행 문자 집합은 모든 전처리 단계 후 컴파일 단계에 입력 되는 프로그램의 텍스트에 사용 되는 인코딩입니다. 이 문자 집합은 컴파일된 코드에서 모든 문자열 또는 문자 리터럴의 내부 표현에 사용 됩니다. 원본 파일에 기본 실행 문자 집합에서 표현할 수 없는 문자가 포함 된 경우 사용할 확장 된 실행 문자 집합을 지정 하려면이 옵션을 설정 합니다. IANA 또는 ISO 문자 집합 이름 또는 점 (.) 뒤에 3 ~ 5 자리 10 진수 코드 페이지 식별자를 사용 하 여 사용할 문자 집합을 지정할 수 있습니다. 지원 되는 코드 페이지 식별자 및 문자 집합 이름 목록은 [코드 페이지 식별자](/windows/win32/Intl/code-page-identifiers)를 참조 하세요.

기본적으로 Visual Studio는 바이트 순서 표시를 검색 하 여 원본 파일이 인코딩된 유니코드 형식 (예: UTF-16 또는 u t f-8) 인지 확인 합니다. 바이트 순서 표시를 찾을 수 없는 경우 **/c-charset** 옵션 또는 **/utf-8** 옵션을 사용 하 여 문자 집합 이름 또는 코드 페이지를 지정 하지 않은 경우 현재 사용자 코드 페이지를 사용 하 여 원본 파일이 인코딩된 것으로 가정 합니다. Visual Studio에서는 여러 문자 인코딩 중 하나를 사용 하 여 c + + 소스 코드를 저장할 수 있습니다. 소스 및 실행 문자 집합에 대 한 자세한 내용은 언어 설명서에서 [문자 집합](../../cpp/character-sets.md) 을 참조 하세요.

소스 문자 집합과 실행 문자 집합을 u t f-8로 설정 하려는 경우 **/utf-8** 컴파일러 옵션을 바로 가기로 사용할 수 있습니다. 명령줄에서 **/source-charset: utf-8/source-charset: u t f-8** 을 지정 하는 것과 같습니다. 이러한 옵션을 사용 하면 기본적으로 **/validate-charset** 옵션이 사용 됩니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**, **C/c + +**, **명령줄** 폴더를 확장 합니다.

1. **추가 옵션** 에서 **/execution-charset** 옵션을 추가 하 고 기본 설정 인코딩을 지정 합니다.

1. **확인** 을 선택하여 변경 내용을 저장합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[/source-charset (소스 문자 집합 설정)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (원본 및 실행 파일 문자 집합을 u t f-8로 설정)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset(호환 문자에 대한 유효성 검사)](validate-charset-validate-for-compatible-characters.md)
