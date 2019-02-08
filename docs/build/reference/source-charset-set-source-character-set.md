---
title: /source-charset (소스 문자 집합 설정)
ms.date: 02/06/2019
f1_keywords:
- source-charset
- /source-charset
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
ms.openlocfilehash: 2a204000be6e4e434b6ef4aabf6bbc0db1593fb0
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849719"
---
# <a name="source-charset-set-source-character-set"></a>/source-charset (소스 문자 집합 설정)

소스 문자 집합에 대 한 실행 파일을 지정할 수 있습니다.

## <a name="syntax"></a>구문

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>인수

**IANA_name**<br/>
IANA 정의한 문자 집합 이름입니다.

**CPID**<br/>
10 진수 숫자로 코드 페이지 식별자입니다.

## <a name="remarks"></a>설명

사용할 수는 **/source-charset** 기본 소스 문자 집합의 표현 되지 않는 문자를 포함 하는 소스 파일을 사용 하는 확장 된 원본 문자 집합을 지정 하는 옵션입니다. 소스 문자 집합 인코딩을 컴파일 전에 전처리 단계에 대 한 입력으로 사용 되는 내부 표현으로 프로그램의 원본 텍스트를 해석 하는 데 사용 됩니다. 내부 표현 실행 파일에 문자열 및 문자 값을 저장 하는 실행 문자 집합 변환 됩니다. IANA 중 하나를 사용할 수 있습니다 또는 ISO 문자 집합 이름을 사용 하도록 설정 하는 문자를 지정 하려면 3 ~ 5 자리 10 진수 코드 페이지 식별자가 뒤에 점 (.). 문자 집합 이름 목록이 지원 코드 페이지 식별자를 참조 하세요 [코드 페이지 식별자](/windows/desktop/Intl/code-page-identifiers)합니다.

Visual Studio는 기본적으로 인지 하는 경우 소스 파일 인코딩된 유니코드 형식으로 예를 들어, utf-16 또는 u t F-8 바이트 순서 표시를 검색 합니다. 바이트 순서 표시가 없는 경우 소스 파일은 인코딩된 현재 사용자 코드 페이지를 사용 하는 문자를 사용 하 여 이름 또는 코드 페이지 집합을 지정 하지 않으면 가정 합니다 **/source-charset** 옵션입니다. Visual Studio를 사용 하면 여러 문자 인코딩 중 하나를 사용 하 여 c + + 소스 코드를 저장할 수 있습니다. 소스 및 실행 문자 집합에 대 한 자세한 내용은 참조 하세요. [문자 집합](../../cpp/character-sets.md) 언어 설명서에 있습니다.

제공한 소스 문자 집합에 문자 집합에 동일한 코드 포인트에 7 비트 ASCII 문자를 매핑해야 또는 많은 컴파일 오류를 따르는 경우가 많습니다. 소스 문자 집합에 확장 된 유니코드 문자 u t F-8로 인코딩할 수 집합으로 매핑 가능한 수도 있어야 합니다. U t F-8에서 인코딩할 수 없는 문자는 구현 별 대체 하 여 표시 됩니다. Microsoft 컴파일러는 이러한 문자는 물음표를 사용합니다.

소스 문자 집합과 실행 문자 집합 모두 u t F-8로 설정 하려는 경우 사용할 수 있습니다 합니다 **/utf-8** 바로 가기로 컴파일러 옵션입니다. 지정 하는 것과 같습니다 **원본-charset:utf-8 /execution-charset:utf-8** 명령줄에서. 이러한 옵션도 사용 하도록 설정 합니다 **/validate-charset** 옵션이 기본적으로 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. 확장 된 **구성 속성**, **C/c + +** 를 **명령줄** 폴더입니다.

1. **추가 옵션**를 추가 합니다 **/source-charset** 옵션을 선택한 기본 인코딩을 지정 합니다.

1. **확인**을 선택하여 변경 내용을 저장합니다.

## <a name="see-also"></a>참고 항목

[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)<br/>
[/execution-charset (실행 문자 집합 설정)](../../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/utf-8(소스 및 실행 파일 문자 집합을 UTF-8로 설정)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset(호환 문자에 대한 유효성 검사)](../../build/reference/validate-charset-validate-for-compatible-characters.md)