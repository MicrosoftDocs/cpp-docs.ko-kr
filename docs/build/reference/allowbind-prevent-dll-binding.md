---
description: 자세한 정보:/ALLOWBIND (DLL 바인딩 방지)
title: /ALLOWBIND(DLL 바인딩 방지)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
ms.openlocfilehash: 727f1cae7d1b0a94a8f7faba90ee6994df8657e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187236"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND(DLL 바인딩 방지)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>설명

/ALLOWBIND:NO는 DLL의 헤더에서 이미지 바인딩을 허용하지 않는 Bind.exe를 가리키는 비트를 설정합니다. 바인딩이 서명을 무효화하므로 디지털 서명된 경우 DLL을 바인딩하지 않으려고 할 수 있습니다.

EDITBIN 유틸리티의 [/allowbind](allowbind.md) 옵션을 사용 하 여/allowbind 기능에 대 한 기존 DLL을 편집할 수 있습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**, **링커** 를 확장 하 고 **명령줄** 을 선택 합니다.

1. `/ALLOWBIND:NO` **추가 옵션** 을 입력 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)<br/>
[BindImage 함수](/windows/win32/api/imagehlp/nf-imagehlp-bindimage)<br/>
[BindImageEx 함수](/windows/win32/api/imagehlp/nf-imagehlp-bindimageex)
