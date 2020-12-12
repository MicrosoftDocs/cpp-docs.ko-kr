---
description: 자세히 알아보기:/E (stdout으로 전처리)
title: /E(stdout으로 전처리)
ms.date: 11/04/2016
f1_keywords:
- /e
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
ms.openlocfilehash: 9d6c9ea3a5fcf8e7ba06ede6e7e70d933b5c921a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192611"
---
# <a name="e-preprocess-to-stdout"></a>/E(stdout으로 전처리)

C 및 c + + 소스 파일을 전처리 하 고 전처리 된 파일을 표준 출력 장치에 복사 합니다.

## <a name="syntax"></a>구문

```
/E
```

## <a name="remarks"></a>설명

이 프로세스에서는 모든 전처리기 지시문이 수행 되 고 매크로 확장이 수행 되며 주석이 제거 됩니다. 전처리 된 출력에서 주석을 유지 하려면 [/c (전처리 중에 주석 유지)](c-preserve-comments-during-preprocessing.md) 컴파일러 옵션을 사용 합니다.

**/E** `#line` 조건부 컴파일에 대 한 전처리기 지시문에 의해 제거 된 각 포함 된 파일의 시작과 끝에 있는 출력에 지시문을 추가 합니다. 이러한 지시문은 전처리 된 파일의 줄 번호를 다시 매깁니다. 따라서 이후 처리 단계 중에 생성 된 오류는 전처리 된 파일의 줄이 아니라 원래 소스 파일의 줄 번호를 나타냅니다.

**/E** 옵션은 컴파일을 표시 하지 않습니다. 컴파일을 위해 전처리 된 파일을 다시 전송 해야 합니다. **/E** 는 **/fa**, **/fa** 및 **/fm** 옵션의 출력 파일도 표시 하지 않습니다. 자세한 내용은 [/fa,/fa (목록 파일)](fa-fa-listing-file.md) 및 [/fm (맵 파일 이름)](fm-name-mapfile.md)을 참조 하세요.

지시문을 표시 하지 않으려면 `#line` [/ep (#line 지시문 없이 Stdout로 전처리)](ep-preprocess-to-stdout-without-hash-line-directives.md) 옵션을 대신 사용 합니다.

전처리 된 출력을 대신 파일로 보내려면 `stdout` 대신 [/P (파일에 대 한 전처리)](p-preprocess-to-a-file.md) 옵션을 사용 합니다.

지시문을 표시 하지 않고 `#line` 전처리 된 출력을 파일로 보내려면 **/P** 와 **/ep** 를 함께 사용 합니다.

미리 컴파일된 헤더는 **/e** 옵션과 함께 사용할 수 없습니다.

별도의 파일로 전처리 하는 경우 토큰 뒤에 공백을 내보내지 않습니다. 이로 인해 잘못 된 프로그램이 발생 하거나 의도 하지 않은 부작용이 발생할 수 있습니다. 다음 프로그램은 성공적으로 컴파일됩니다.

```
#define m(x) x
m(int)main( )
{
   return 0;
}
```

그러나를 사용 하 여 컴파일하는 경우

```
cl -E test.cpp > test2.cpp
```

`int main` test2에서는 잘못 `intmain` 되었습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>을 참조하세요.

## <a name="example"></a>예제

다음 명령줄은 전처리 하 고 `ADD.C` , 주석을 유지 하 `#line` 고, 지시문을 추가 하 고, 표준 출력 장치에 결과를 표시 합니다.

```
CL /E /C ADD.C
```

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
