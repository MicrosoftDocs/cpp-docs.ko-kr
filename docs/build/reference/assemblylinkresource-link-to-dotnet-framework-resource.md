---
description: 자세히 알아보기:/ASSEMBLYLINKRESOURCE (.NET Framework 리소스에 대 한 링크)
title: /ASSEMBLYLINKRESOURCE(.NET Framework 리소스에 대한 링크)
ms.date: 11/04/2016
f1_keywords:
- /ASSEMBLYLINKRESOURCE
- VC.Project.VCLinkerTool.AssemblyLinkResource
helpviewer_keywords:
- -ASSEMBLYLINKRESOURCE linker option
- ASSEMBLYLINKRESOURCE linker option
- /ASSEMBLYLINKRESOURCE linker option
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
ms.openlocfilehash: 32761cb16e8428d5e3c18330dffb49a50a42903c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183011"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE(.NET Framework 리소스에 대한 링크)

```
/ASSEMBLYLINKRESOURCE:filename
```

## <a name="arguments"></a>인수

*filename*<br/>
어셈블리에서 연결할 .NET Framework 리소스 파일입니다.

## <a name="remarks"></a>설명

/ASSEMBLYLINKRESOURCE 옵션은 출력 파일에 .NET Framework 리소스에 대 한 링크를 만듭니다. 리소스 파일은 출력 파일에 배치 되지 않습니다. [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) 는 출력 파일에 리소스 파일을 포함 합니다.

연결 된 리소스는 링커를 사용 하 여 만들 때 어셈블리에서 public입니다.

/ASSEMBLYLINKRESOURCE를 사용 하려면 컴파일에 [/clr](clr-common-language-runtime-compilation.md)을 포함 해야 합니다. /ASSEMBLYLINKRESOURCE.에는 [/LN](ln-create-msil-module.md) 또는 [/noassembly](noassembly-create-a-msil-module.md) 를 사용할 수 없습니다.

*Filename* 이 개발 환경에서 [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) 또는 개발 환경에서 만들어진 .NET Framework 리소스 파일인 경우에는 **system.object** 네임 스페이스의 멤버를 사용 하 여 액세스할 수 있습니다. 자세한 내용은 [system.object](/dotnet/api/system.resources.resourcemanager)를 참조 하십시오. 다른 모든 리소스의 경우에는  \* 런타임에 리소스에 액세스 하기 위해 **System.object** 클래스의 getmanifestresource 메서드를 사용 합니다.

*filename* 은 모든 파일 형식일 수 있습니다. 예를 들어 어셈블리의 네이티브 DLL 부분을 만들어 전역 어셈블리 캐시에 설치 하 고 어셈블리의 관리 코드에서 액세스할 수 있습니다.

어셈블리 생성에 영향을 주는 다른 링커 옵션은 다음과 같습니다.

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 옵션을 입력 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
