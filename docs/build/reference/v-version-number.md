---
description: 자세히 알아보기:/V (버전 번호)
title: /V(버전 번호)
ms.date: 11/04/2016
f1_keywords:
- /v
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
ms.openlocfilehash: 5025642d4ae30315d24754a7ee46268050cfb22a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187054"
---
# <a name="v-version-number"></a>/V(버전 번호)

더 이상 사용되지 않습니다. 텍스트 문자열을 .obj 파일에 포함 합니다.

## <a name="syntax"></a>구문

```
/Vstring
```

## <a name="arguments"></a>인수

*string*<br/>
.Obj 파일에 포함할 버전 번호 또는 저작권 표시를 지정 하는 문자열입니다.

## <a name="remarks"></a>설명

Stringcan 버전 번호 또는 저작권 표시를 사용 하 여 .obj 파일에 레이블을 지정할 수 있습니다. 문자열의 일부인 경우 공백 또는 탭 문자를 큰따옴표 (")로 묶어야 합니다. 백슬래시 ( \\ )는 문자열의 일부인 경우 큰따옴표 앞에와 야 합니다. **/V** 와 사이의 공백은 `string` 선택 사항입니다.

컴파일러 주석 형식 인수를 사용 하 여 [주석 (c/c + +)](../../preprocessor/comment-c-cpp.md) 을 사용 하 여 .obj 파일에 컴파일러의 이름과 버전 번호를 추가할 수도 있습니다.

**/V** 옵션은 Visual Studio 2005부터 더 이상 사용 되지 않습니다. **/V** 는 주로 vxds (가상 장치 드라이버) 빌드를 지 원하는 데 사용 되 고, vxds 빌드는 Visual C++ 도구 집합에서 더 이상 지원 되지 않습니다. 사용 되지 않는 컴파일러 옵션의 목록은 [컴파일러 옵션 범주별](compiler-options-listed-by-category.md)목록에서 **사용 되지 않는 컴파일러 옵션** 을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
