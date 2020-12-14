---
description: 자세한 정보:/Fm (맵 파일 이름)
title: /Fm(맵 파일 이름 지정)
ms.date: 11/04/2016
f1_keywords:
- /fm
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
ms.openlocfilehash: 5c86a18ae9880a499997bcac2d8411859753d858
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200483"
---
# <a name="fm-name-mapfile"></a>/Fm(맵 파일 이름 지정)

해당 .exe 파일이 나 DLL에 표시 되는 순서 대로 세그먼트 목록을 포함 하는 맵 파일을 생성 하도록 링커에 지시 합니다.

## <a name="syntax"></a>구문

```
/Fmpathname
```

## <a name="remarks"></a>설명

기본적으로 맵 파일에는를 사용 하 여 해당 C 또는 c + + 소스 파일의 기본 이름이 지정 됩니다. 맵 확장.

**/Fm** 을 지정 하면 [/Map (맵 파일 생성)](map-generate-mapfile.md) 링커 옵션을 지정한 것과 동일한 효과가 있습니다.

링크를 표시 하지 [않는/c (링크 없이 컴파일)](c-compile-without-linking.md) 를 지정 하는 경우 **/fm** 은 적용 되지 않습니다.

일반적으로 맵 파일의 전역 기호는 변수 이름에 선행 밑줄을 추가 하기 때문에 하나 이상의 선행 밑줄이 있습니다. 맵 파일에 표시 되는 많은 전역 기호는 컴파일러 및 표준 라이브러리에서 내부적으로 사용 됩니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[출력 파일 (/F) 옵션](output-file-f-options.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[경로 이름 지정](specifying-the-pathname.md)
