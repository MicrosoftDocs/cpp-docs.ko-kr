---
description: 자세히 알아보기:/INCLUDE (강제 기호 참조)
title: /INCLUDE(강제 기호 참조)
ms.date: 11/04/2016
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
ms.openlocfilehash: 4938f5e92f91718f522df103303e6382005d463c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191305"
---
# <a name="include-force-symbol-references"></a>/INCLUDE(강제 기호 참조)

```
/INCLUDE:symbol
```

## <a name="parameters"></a>매개 변수

*화살표*<br/>
기호 테이블에 추가할 기호를 지정 합니다.

## <a name="remarks"></a>설명

/INCLUDE 옵션은 지정 된 기호를 기호 테이블에 추가 하도록 링커에 지시 합니다.

여러 기호를 지정 하려면 쉼표 (,), 세미콜론 (;) 또는 기호 이름 사이에 공백을 입력 합니다. 명령줄에서 `symbol` 각 기호에 대해/INCLUDE를 한 번씩 지정 합니다.

링커에서 `symbol` 기호 정의를 포함 하는 개체를 프로그램에 추가 하 여 확인 합니다. 이 기능은 다른 방법으로는 프로그램에 연결 되지 않는 라이브러리 개체를 포함 하는 데 유용 합니다.

이 옵션을 사용 하 여 기호를 지정 하면 해당 기호의 제거를 [/opt: REF](opt-optimizations.md)로 재정의 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **입력** 속성 페이지를 클릭 합니다.

1. **Force Symbol References** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
