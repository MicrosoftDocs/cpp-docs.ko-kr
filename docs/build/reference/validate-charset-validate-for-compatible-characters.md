---
description: 자세한 정보:/validate-charset (호환 되는 문자 유효성 검사)
title: /validate-charset(호환 문자에 대한 유효성 검사)
ms.date: 02/06/2019
f1_keywords:
- /validate-charset
- validate-charset
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
ms.openlocfilehash: bda69c59fc89aae5028543ba579ee1e0b70f67e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250402"
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/validate-charset(호환 문자에 대한 유효성 검사)

소스 파일 텍스트에 u t f-8로 표현 되는 문자만 포함 되어 있는지 확인 합니다.

## <a name="syntax"></a>구문

```
/validate-charset[-]
```

## <a name="remarks"></a>설명

**/Validate-charset** 옵션을 사용 하 여 소스 코드에 소스 문자 집합과 실행 문자 집합 모두에서 표현할 수 있는 문자만 포함 되어 있는지 확인할 수 있습니다. 이 검사는 **/source-charset**, **/source-charset** 또는 **/utf-8** 컴파일러 옵션을 지정 하면 자동으로 사용 됩니다. **/Validate-charset-** 을 지정 하 여이 검사를 명시적으로 사용 하지 않도록 설정할 수 있습니다.

기본적으로 Visual Studio는 바이트 순서 표시를 검색 하 여 원본 파일이 인코딩된 유니코드 형식 (예: UTF-16 또는 u t f-8) 인지 확인 합니다. 바이트 순서 표시가 없는 경우 **/utf-8** 또는 **/source-charset** 옵션을 사용 하 여 코드 페이지를 지정 하지 않으면 현재 사용자 코드 페이지를 사용 하 여 소스 파일이 인코딩된 것으로 가정 합니다. Visual Studio에서는 여러 문자 인코딩 중 하나를 사용 하 여 c + + 소스 코드를 저장할 수 있습니다. 소스 및 실행 문자 집합에 대 한 자세한 내용은 언어 설명서에서 [문자 집합](../../cpp/character-sets.md) 을 참조 하세요. 지원 되는 코드 페이지 식별자 및 문자 집합 이름 목록은 [코드 페이지 식별자](/windows/win32/Intl/code-page-identifiers)를 참조 하세요.

Visual Studio는 소스 문자 집합과 실행 문자 집합 간에 변환 하는 동안 내부 문자 인코딩으로 u t f-8을 사용 합니다. 소스 파일의 문자를 실행 문자 집합에 표시할 수 없는 경우 UTF-8 변환은 물음표 '? ' 문자를 대체 합니다. **/Validate-charset** 옵션을 선택 하면이 문제가 발생 하는 경우 컴파일이 경고를 보고 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**, **C/c + +**, **명령줄** 폴더를 확장 합니다.

1. **추가 옵션** 에서 **/validate-charset** 옵션을 추가 하 고 기본 설정 인코딩을 지정 합니다.

1. **확인** 을 선택하여 변경 내용을 저장합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[/sv-ecin 문자 집합 (실행 문자 집합 설정)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (소스 문자 집합 설정)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (원본 및 실행 파일 문자 집합을 u t f-8로 설정)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)
