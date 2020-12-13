---
description: 자세히 알아보기:/Yl (디버그 라이브러리에 PCH 참조 넣기)
title: /Yl(디버그 라이브러리에 PCH 참조 넣기)
ms.date: 01/29/2018
f1_keywords:
- /yl
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
ms.openlocfilehash: f1d05b4e0c38377233e9aaf6299227f7fbaebd55
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151855"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl(디버그 라이브러리에 PCH 참조 넣기)

**/Yl** 옵션을 사용 하면 미리 컴파일된 헤더 파일에 고유한 기호가 생성 되 고,이 기호에 대 한 참조는 미리 컴파일된 헤더를 사용 하는 모든 개체 파일에 삽입 됩니다.

## <a name="syntax"></a>Syntax

>**/Yl**\
>**/Yl**_이름_\
>**Yl**

### <a name="arguments"></a>인수

*name*<br/>
고유 기호의 일부로 사용 되는 선택적 이름입니다.

*\-*<br/>
대시 (-)는 **/Yl** 컴파일러 옵션을 명시적으로 사용 하지 않도록 설정 합니다.

## <a name="remarks"></a>설명

**/Yl** 컴파일러 옵션은 [/yc](yc-create-precompiled-header-file.md) 옵션을 사용 하 여 만든 미리 컴파일된 헤더 파일에 고유한 기호 정의를 만듭니다. 이 기호에 대 한 참조는 [/yu](yu-use-precompiled-header-file.md) 컴파일러 옵션을 사용 하 여 미리 컴파일된 헤더를 포함 하는 모든 파일에 자동으로 삽입 됩니다. 미리 컴파일된 헤더 파일을 만드는 데 **/yc** 를 사용 하는 경우 **/Yl** 옵션은 기본적으로 사용 하도록 설정 됩니다.

**/Yl**_name_ 옵션은 미리 컴파일된 헤더 파일에 식별할 수 있는 기호를 만드는 데 사용 됩니다. 컴파일러는에서 만든 데코레이팅된 기호 이름의 일부로 *name* 인수를 사용 합니다 `__@@_PchSym_@00@...@name` . 여기서 줄임표 (...)는 고유한 컴파일러 생성 문자열을 나타냅니다. *Name* 인수를 생략 하면 컴파일러가 기호 이름을 자동으로 생성 합니다. 일반적으로 기호의 이름을 알 필요가 없습니다. 그러나 프로젝트에서 미리 컴파일된 헤더 파일을 둘 이상 사용 하는 경우 **/Yl**_name_ 옵션은 미리 컴파일된 헤더를 사용 하는 개체 파일을 확인 하는 데 유용할 수 있습니다. *이름을* 검색 문자열로 사용 하 여 덤프 파일에서 기호 참조를 찾을 수 있습니다.

**/Yl-** 는 기본 동작을 사용 하지 않도록 설정 하 고 미리 컴파일된 헤더 파일에 식별 기호를 넣지 않습니다. 이 미리 컴파일된 헤더를 포함 하는 컴파일된 파일은 일반적인 기호 참조를 가져오지 않습니다.

**/Yc** 를 지정 하지 않으면 **/Yl** 옵션은 아무런 영향도 미치지 않지만 지정 된 경우에는 **/yc** 가 지정 될 때 전달 되는 모든 **/Yl** 옵션과 일치 해야 합니다.

**/Yl-**, **/Yc** 및 [/z7](z7-zi-zi-debug-information-format.md) 옵션을 사용 하 여 미리 컴파일된 헤더 파일을 작성 하는 경우 별도의 .pdb 파일이 아닌 미리 컴파일된 헤더를 만드는 데 사용 되는 소스 파일에 대 한 개체 파일에 디버깅 정보가 저장 됩니다. 그런 다음이 개체 파일이 라이브러리의 일부가 되 면 미리 컴파일된 헤더 파일을 만드는 데 사용 된 소스 파일이 기호 자체를 정의 하지 않는 경우이 라이브러리와 미리 컴파일된 헤더 파일을 사용 하는 빌드에서 [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) 오류 또는 [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) 경고가 발생할 수 있습니다. 라이브러리 클라이언트에서 참조 되는 개체 파일이 없으면 연결 된 디버깅 정보와 함께 링커가 개체 파일을 연결 된 디버깅 정보와 함께 제외할 수 있습니다. 이 문제를 해결 하려면 **/yc** 를 사용 하 여 미리 컴파일된 헤더 파일을 만들 때 **/Yl** (또는 **/Yl-** 옵션 제거)를 지정 합니다. 이렇게 하면 디버깅 정보를 포함 하는 라이브러리의 개체 파일이 빌드에 연결 됩니다.

미리 컴파일된 헤더에 대 한 자세한 내용은 다음을 참조 하세요.

- [/Y (미리 컴파일된 헤더)](y-precompiled-headers.md)

- [미리 컴파일된 헤더 파일](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에 **/Yl**_name_ 컴파일러 옵션을 추가 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
