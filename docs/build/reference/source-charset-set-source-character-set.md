---
description: 다음에 대 한 자세한 정보:/source-charset (소스 문자 집합 설정)
title: /source-charset (소스 문자 집합 설정)
ms.date: 02/06/2019
f1_keywords:
- source-charset
- /source-charset
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
ms.openlocfilehash: 5ed1ea8e130dd61b4d5903570b781f36856d3e60
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224779"
---
# <a name="source-charset-set-source-character-set"></a>/source-charset (소스 문자 집합 설정)

실행 파일에 대 한 원본 문자 집합을 지정할 수 있습니다.

## <a name="syntax"></a>구문

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>인수

**IANA_name**<br/>
IANA에서 정의한 문자 집합 이름입니다.

**CPID**<br/>
10 진수로 된 코드 페이지 식별자입니다.

## <a name="remarks"></a>설명

원본 파일에 기본 소스 문자 집합에 표시 되지 않는 문자가 포함 된 경우에 사용할 확장 된 소스 문자 집합을 지정 하는 데 **/source-charset** 옵션을 사용할 수 있습니다. 소스 문자 집합은 컴파일 전에 전처리 단계에 대 한 입력으로 사용 된 내부 표현으로 프로그램의 소스 텍스트를 해석 하는 데 사용 되는 인코딩입니다. 그런 다음 내부 표현을 실행 문자 집합으로 변환 하 여 실행 파일에 문자열 및 문자 값을 저장 합니다. IANA 또는 ISO 문자 집합 이름 또는 점 (.) 뒤에 3 ~ 5 자리 10 진수 코드 페이지 식별자를 사용 하 여 사용할 문자 집합을 지정할 수 있습니다. 지원 되는 코드 페이지 식별자 및 문자 집합 이름 목록은 [코드 페이지 식별자](/windows/win32/Intl/code-page-identifiers)를 참조 하세요.

기본적으로 Visual Studio는 바이트 순서 표시를 검색 하 여 원본 파일이 인코딩된 유니코드 형식 (예: UTF-16 또는 u t f-8) 인지 확인 합니다. 바이트 순서 표시가 없는 경우 **/c-charset** 옵션을 사용 하 여 문자 집합 이름 또는 코드 페이지를 지정 하지 않으면 현재 사용자 코드 페이지를 사용 하 여 소스 파일이 인코딩된 것으로 가정 합니다. Visual Studio에서는 여러 문자 인코딩 중 하나를 사용 하 여 c + + 소스 코드를 저장할 수 있습니다. 소스 및 실행 문자 집합에 대 한 자세한 내용은 언어 설명서의 [문자 집합](../../cpp/character-sets.md) 을 참조 하세요.

사용자가 제공 하는 소스 문자 집합은 7 비트 ASCII 문자를 문자 집합의 동일한 코드 점에 매핑해야 하며, 많은 컴파일 오류가 발생할 수 있습니다. 또한 원본 문자 집합을 u t f-8로 encodable 확장 된 유니코드 문자 집합으로 매핑해야 합니다. U t f-8에서 encodable 않는 문자는 구현 별 대체로 표시 됩니다. Microsoft 컴파일러는 이러한 문자에 물음표를 사용 합니다.

소스 문자 집합과 실행 문자 집합을 u t f-8로 설정 하려는 경우 **/utf-8** 컴파일러 옵션을 바로 가기로 사용할 수 있습니다. 명령줄에서 **/source-charset: utf-8/source-charset: u t f-8** 을 지정 하는 것과 같습니다. 이러한 옵션을 사용 하면 기본적으로 **/validate-charset** 옵션이 사용 됩니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**, **C/c + +**, **명령줄** 폴더를 확장 합니다.

1. **추가 옵션** 에서 **/source-charset** 옵션을 추가 하 고 기본 설정 인코딩을 지정 합니다.

1. **확인** 을 선택하여 변경 내용을 저장합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[/sv-ecin 문자 집합 (실행 문자 집합 설정)](execution-charset-set-execution-character-set.md)<br/>
[/utf-8 (원본 및 실행 파일 문자 집합을 u t f-8로 설정)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset(호환 문자에 대한 유효성 검사)](validate-charset-validate-for-compatible-characters.md)
