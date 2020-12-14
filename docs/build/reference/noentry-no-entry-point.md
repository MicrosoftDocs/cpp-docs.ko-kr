---
description: 자세히 알아보기:/NOENTRY (진입점 없음)
title: /NOENTRY(진입점 없음)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ResourceOnlyDLL
- /noentry
helpviewer_keywords:
- entry points [C++], linker specifying
- -NOENTRY linker option
- resource-only DLLs [C++], creating
- NOENTRY linker option
- /NOENTRY linker option [C++]
- DLLs [C++], creating
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
ms.openlocfilehash: c3d1f725a4e185a052d443010894ff2dc2261675
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196687"
---
# <a name="noentry-no-entry-point"></a>/NOENTRY(진입점 없음)

```
/NOENTRY
```

## <a name="remarks"></a>설명

실행 코드가 없는 리소스 전용 DLL을 만들려면 /NOENTRY 옵션을 지정해야 합니다. 자세한 내용은 [Resource-Only DLL 만들기](../creating-a-resource-only-dll.md)를 참조 하세요.

이 옵션을 사용하면 LINK가 `_main`에 대한 참조를 DLL로 링크하는 것을 방지할 수 있습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **링커** 폴더를 선택 합니다.

1. **고급** 속성 페이지를 클릭합니다.

1. **항목 점 없음** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[Resource-Only DLL 만들기](../creating-a-resource-only-dll.md)<br/>
[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
