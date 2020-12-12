---
description: 자세히 알아보기:/ASSEMBLYDEBUG (DebuggableAttribute 추가)
title: /ASSEMBLYDEBUG(DebuggableAttribute 추가)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AssemblyDebug
- /ASSEMBLYDEBUG
helpviewer_keywords:
- /ASSEMBLYDEBUG linker option
- -ASSEMBLYDEBUG linker option
- ASSEMBLYDEBUG linker option
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
ms.openlocfilehash: 7d63ae4ffd86099147b076a499321ed5dcf3ca54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183037"
---
# <a name="assemblydebug-add-debuggableattribute"></a>/ASSEMBLYDEBUG(DebuggableAttribute 추가)

```
/ASSEMBLYDEBUG[:DISABLE]
```

/ASSEMBLYDEBUG는 디버그 정보 추적을 사용 하 여 **DebuggableAttribute** 특성을 내보내고 JIT 최적화를 사용 하지 않도록 설정 합니다. 이는 원본에서 다음 특성을 지정 하는 것과 같습니다.

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

/ASSEMBLYDEBUG: DISABLE은 **DebuggableAttribute** 특성을 내보내고 디버그 정보 추적을 사용 하지 않도록 설정 하 고 JIT 최적화를 사용 하도록 설정 합니다. 이는 원본에서 다음 특성을 지정 하는 것과 같습니다.

```
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE
```

기본값은 **DebuggableAttribute** 특성을 내보내지 않는 것입니다.

DebuggableAttribute는 소스 코드에서 직접 어셈블리에 추가할 수도 있습니다. 예를 들면 다음과 같습니다.

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

## <a name="remarks"></a>설명

관리 되는 이미지를 디버깅할 수 있도록 명시적으로 지정 해야 합니다. [/Zi](z7-zi-zi-debug-information-format.md) 만 사용 해도 충분 하지 않습니다.

어셈블리 생성에 영향을 주는 다른 링커 옵션은 다음과 같습니다.

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **디버그** 속성 페이지를 클릭 합니다.

1. 디버깅 가능한 **어셈블리** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
