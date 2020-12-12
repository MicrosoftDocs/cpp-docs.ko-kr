---
description: 자세히 알아보기:/ASSEMBLYMODULE (MSIL 모듈을 어셈블리에 추가)
title: /ASSEMBLYMODULE(MSIL 모듈을 어셈블리에 추가)
ms.date: 11/04/2016
f1_keywords:
- /assemblymodule
- VC.Project.VCLinkerTool.AddModuleNamesToAssembly
helpviewer_keywords:
- ASSEMBLYMODULE linker option
- assemblies [C++], adding modules to
- assemblies [C++]
- /ASSEMBLYMODULE linker option
- -ASSEMBLYMODULE linker option
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
ms.openlocfilehash: d56895b6bec05efda1104e319e93a040f818e06e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182946"
---
# <a name="assemblymodule-add-a-msil-module-to-the-assembly"></a>/ASSEMBLYMODULE(MSIL 모듈을 어셈블리에 추가)

```
/ASSEMBLYMODULE:filename
```

## <a name="arguments"></a>인수

*filename*<br/>
이 어셈블리에 포함 하려는 모듈입니다.

## <a name="remarks"></a>설명

/ASSEMBLYMODULE 옵션을 사용 하면 어셈블리에 모듈 참조를 추가할 수 있습니다. 모듈의 형식 정보는 모듈 참조를 추가한 어셈블리 프로그램에서 사용할 수 없습니다. 그러나 모듈의 형식 정보는 어셈블리를 참조 하는 모든 프로그램에서 사용할 수 있습니다.

[#Using](../../preprocessor/hash-using-directive-cpp.md) 를 사용 하 여 어셈블리에 모듈 참조를 추가 하 고 어셈블리 프로그램에서 모듈의 형식 정보를 사용할 수 있도록 합니다.

예를 들어 다음 시나리오를 고려할 수 있습니다.

1. [/LN](ln-create-msil-module.md)를 사용 하 여 모듈을 만듭니다.

1. 다른 프로젝트에서/ASSEMBLYMODULE를 사용 하 여 어셈블리를 만드는 현재 컴파일에 모듈을 포함 합니다. 이 프로젝트는를 사용 하 여 모듈을 참조 하지 않습니다 `#using` .

1. 이제이 어셈블리를 참조 하는 모든 프로젝트에서 모듈의 형식을 사용할 수 있습니다.

어셈블리 생성에 영향을 주는 다른 링커 옵션은 다음과 같습니다.

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

MSVC 링커는 .netmodule 파일을 입력으로 사용 하 고 링커에 의해 생성 된 출력 파일은 어셈블리 또는 .netmodule이 되며 링커에 대 한 입력 된 .netmodules에 대 한 런타임 종속성이 없습니다.  자세한 내용은 [링커 입력 파일로 사용하는 .netmodule 파일](netmodule-files-as-linker-input.md)을 참조하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **입력** 속성 페이지를 클릭 합니다.

1. **어셈블리에 모듈 추가** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
