---
description: 자세히 알아보기:/ASSEMBLYRESOURCE (관리 되는 리소스 포함)
title: /ASSEMBLYRESOURCE(관리되는 리소스 포함)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
ms.openlocfilehash: 3f79cc177df72bb83288a0a229fdf47adb0e7fc0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182920"
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE(관리되는 리소스 포함)

```
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]
```

## <a name="parameters"></a>매개 변수

*filename*<br/>
이 어셈블리에 포함 하려는 관리 되는 리소스입니다.

*name*<br/>
선택 사항입니다. 리소스의 논리적 이름입니다. 리소스를 로드 하는 데 사용 되는 이름입니다. 기본값은 파일 이름입니다.

필요에 따라 어셈블리 매니페스트에서 파일이 개인 파일 인지 여부를 지정할 수 있습니다. 기본적으로 *이름은* 어셈블리에서 public입니다.

## <a name="remarks"></a>설명

/ASSEMBLYRESOURCE 옵션을 사용 하 여 어셈블리에 리소스를 포함 합니다.

리소스는 링커를 사용 하 여 만들 때 어셈블리에서 public입니다. 링커를 사용 하 여 어셈블리에 있는 리소스의 이름을 바꿀 수 없습니다.

예를 들어 *filename* 이 리소스 [파일 생성기 (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) 나 개발 환경에서 만들어진 .NET Framework 리소스 (.resources) 파일인 경우 **system.xml 네임 스페이스의 멤버** 를 사용 하 여 액세스할 수 있습니다 (자세한 내용은 [system.object](/dotnet/api/system.resources.resourcemanager) 참조). 다른 모든 리소스의 경우에  \* 는 런타임에 리소스에 액세스 하기 위해 **System.object** 클래스의 getmanifestresource 메서드를 사용 합니다.

어셈블리 생성에 영향을 주는 다른 링커 옵션은 다음과 같습니다.

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **입력** 속성 페이지를 클릭 합니다.

1. **관리 되는 리소스 파일 포함** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
