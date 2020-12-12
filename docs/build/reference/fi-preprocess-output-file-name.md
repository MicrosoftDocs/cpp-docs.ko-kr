---
description: '자세히 알아보기: `/Fi` (출력 파일 이름 전처리)'
title: /Fi (출력 파일 이름 전처리)
ms.date: 08/12/2020
f1_keywords:
- /Fi
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
ms.openlocfilehash: c598730b19b843aa312df71d745ed363d082cc43
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192228"
---
# <a name="fi-preprocess-output-file-name"></a>`/Fi` (출력 파일 이름 전처리)

[ `/P` (파일 전처리)](p-preprocess-to-a-file.md) 컴파일러 옵션에서 전처리 된 출력을 쓰는 출력 파일의 이름을 지정 합니다.

## <a name="syntax"></a>구문

> **`/Fi`**_`pathname`_

### <a name="parameters"></a>매개 변수

*`pathname`*\
컴파일러 옵션에 의해 생성 되는 출력 파일의 상대 또는 절대 경로 및 파일 이름입니다 **`/P`** . 또는 둘 *`.i`* 이상의 입력 파일이 지정 된 경우 출력 파일의 디렉터리 경로입니다. 옵션과 사이에 공백을 넣지 마십시오 **`/Fi`** *`pathname`* .

## <a name="remarks"></a>설명

컴파일러 옵션과 **`/Fi`** 함께 컴파일러 옵션을 사용 **`/P`** 합니다. **`/P`** 을 지정 하지 않으면 **`/Fi`** 명령줄 경고 D9007이 발생 합니다.

매개 변수에 대 한 디렉터리 경로 (백슬래시로 끝나는 경로)만 지정 하는 경우 **`\`** *`pathname`* 소스 파일의 기본 이름이 전처리 된 출력 파일의 기본 이름으로 사용 됩니다. *`pathname`* 매개 변수에는 특정 파일 이름 확장명이 필요 하지 않습니다. 그러나 파일 이름 확장명을 지정 하지 않으면 ". i" 확장이 사용 됩니다.

### <a name="example"></a>예제

다음 명령줄은 전처리 하 고 *`PROGRAM.cpp`* , 주석을 유지 하 [`#line`](../../preprocessor/hash-line-directive-c-cpp.md) 고, 지시문을 추가 하 고, 결과를 파일에 씁니다 *`MYPROCESS.i`* .

```cmd
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

이 명령줄 *`main.cpp`* *`helper.cpp`* *`main.i`* *`helper.i`* 은 라는 하위 디렉터리에서 및에 전처리 됩니다 *`preprocessed`* .

```cmd
CL /P /Fi".\\preprocessed\\" main.cpp helper.cpp
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 소스 파일 또는 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **전처리기** 속성 페이지를 선택 합니다.

1. **파일 전처리** 속성을 **예** 로 설정 합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **`/Fi`** *`pathname`* **추가 옵션** 상자에 컴파일러 옵션을 입력 합니다. 프로젝트에 대해이 속성을 설정할 때 파일 이름이 아니라 디렉터리 경로만 지정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[`/P` (파일로 전처리)](p-preprocess-to-a-file.md)<br/>
[경로 이름 지정](specifying-the-pathname.md)
