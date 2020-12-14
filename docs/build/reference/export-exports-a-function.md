---
description: 자세히 알아보기:/EXPORT (함수 내보내기)
title: /EXPORT(함수 내보내기)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
ms.openlocfilehash: a52ea79d0569d31c26eabd06d51ef58a10567119
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200808"
---
# <a name="export-exports-a-function"></a>/EXPORT(함수 내보내기)

프로그램에서 이름 또는 서 수 또는 데이터를 기준으로 함수를 내보냅니다.

## <a name="syntax"></a>Syntax

> **/Export:**<em>entryname</em>[**, \@**<em>ordinal</em>[**, NONAME**]] [**, DATA**]

## <a name="remarks"></a>설명

**/Export** 옵션은 다른 프로그램에서 함수를 호출 하거나 데이터를 사용할 수 있도록 프로그램에서 내보낼 함수 또는 데이터 항목을 지정 합니다. 내보내기는 일반적으로 DLL에 정의 됩니다.

*Entryname* 은 호출 프로그램에서 사용할 함수 또는 데이터 항목의 이름입니다. *서 수* 는 1에서 65535 사이의 내보내기 테이블에 인덱스를 지정 합니다. *서 수* 를 지정 하지 않으면 LINK에서 1을 할당 합니다. **NONAME** 키워드는 *entryname* 없이 서 수로만 함수를 내보냅니다.

**Data** 키워드는 내보낸 항목이 데이터 항목 임을 지정 합니다. 클라이언트 프로그램의 데이터 항목은 **dllimport (extern __declspec)** 를 사용 하 여 선언 해야 합니다.

정의를 내보내는 방법에는 다음 네 가지 방법이 있습니다. 권장 되는 사용 순서 대로 나열 됩니다.

1. 소스 코드의 [__declspec (dllexport)](../../cpp/dllexport-dllimport.md)

1. .Def 파일의 [EXPORTS](exports.md) 문

1. LINK 명령의 /EXPORT 사양

1. 폼의 소스 코드에 있는 [주석](../../preprocessor/comment-c-cpp.md) 지시문 `#pragma comment(linker, "/export: definition ")` 입니다.

이러한 모든 메서드는 동일한 프로그램에서 사용할 수 있습니다. LINK가 내보내기를 포함 하는 프로그램을 빌드하는 경우 빌드에서 .exp 파일을 사용 하지 않는 한 가져오기 라이브러리도 만듭니다.

링크에서 데코레이팅된 형식의 식별자를 사용 합니다. 컴파일러는 .obj 파일을 만들 때 식별자를 데코 레이트 합니다. *Entryname* 가 소스 코드에 표시 되는 데코레이팅되지 않은 형식으로 링커에 지정 된 경우 링크는 이름과 일치 하도록 시도 합니다. 고유한 일치 항목을 찾을 수 없는 경우 링크에서 오류 메시지를 발행 합니다. 링커에 대해 지정 해야 하는 경우 [DUMPBIN](dumpbin-reference.md) 도구를 사용 하 여 식별자의 [데코레이팅된 이름](decorated-names.md) 형식을 가져옵니다.

> [!NOTE]
> 또는로 선언 된 C 식별자의 데코레이팅된 형식을 지정 하지 마세요 **`__cdecl`** **`__stdcall`** .

데코레이팅되지 않은 함수 이름을 내보내야 하 고 빌드 구성에 따라 다른 내보내기를 포함 하는 경우 (예: 32 비트 또는 64 비트 빌드) 각 구성에 대해 서로 다른 DEF 파일을 사용할 수 있습니다. 전처리기 조건부 지시문은 DEF 파일에서 사용할 수 없습니다. 또는 `#pragma comment` 여기에 표시 된 것 처럼 함수 선언 앞에 지시문을 사용할 수 있습니다. 여기서 `PlainFuncName` 은 데코레이팅되지 않은 이름이 고 `_PlainFuncName@4` 은 데코레이팅된 함수 이름입니다.

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **링커** > **명령줄** 속성 페이지를 선택합니다.

1. **추가 옵션** 상자에 옵션을 입력 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
