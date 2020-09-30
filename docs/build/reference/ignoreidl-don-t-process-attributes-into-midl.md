---
title: /IGNOREIDL (&#39;t를 MIDL로 처리 하지 않음)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
ms.openlocfilehash: eac6209e0c34562254117d6ab9db5f47545037ea
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506892"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (&#39;t를 MIDL로 처리 하지 않음)

```
/IGNOREIDL
```

## <a name="remarks"></a>설명

/IGNOREIDL 옵션은 소스 코드의 모든 [idl 특성이](../../windows/attributes/idl-attributes.md) .idl 파일에서 처리 되지 않도록 지정 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **포함 된 IDL** 속성 페이지를 클릭 합니다.

1. **포함 IDL 속성 무시** 를 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)<br/>
[/IDLOUT (MIDL 출력 파일 이름)](idlout-name-midl-output-files.md)<br/>
[/TLBOUT (이름. TLB 파일)](tlbout-name-dot-tlb-file.md)<br/>
[/MIDL (MIDL 명령줄 옵션 지정)](midl-specify-midl-command-line-options.md)<br/>
[특성을 사용하는 프로그램 빌드](../../windows/attributes/cpp-attributes-com-net.md)
