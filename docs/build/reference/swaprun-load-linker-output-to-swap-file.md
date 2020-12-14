---
description: 다음에 대 한 자세한 정보:/SWRUN (링커 출력을 스왑 파일로 로드)
title: /SWAPRUN(링커 출력을 스왑 파일로 로드)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.SwapRunFromNet
- /swaprun
- VC.Project.VCLinkerTool.SwapRunFromCD
helpviewer_keywords:
- -SWAPRUN linker option
- files [C++], LINK
- LINK tool [C++], output
- linker [C++], copying output to swap file
- swap file for linker output
- output files, linker
- /SWAPRUN linker option
- SWAPRUN linker option
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
ms.openlocfilehash: f62d5e32432a2c738b7782c0fbf0cd4fd76a7f9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230213"
---
# <a name="swaprun-load-linker-output-to-swap-file"></a>/SWAPRUN(링커 출력을 스왑 파일로 로드)

```
/SWAPRUN:{NET|CD}
```

## <a name="remarks"></a>설명

/SWRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRAP 이는 Windows NT 4.0 이상의 기능입니다.

NET이 지정 된 경우 운영 체제는 먼저 네트워크에서 스왑 파일로 이진 이미지를 복사 하 고 여기에서 로드 합니다. 이 옵션은 네트워크를 통해 응용 프로그램을 실행 하는 데 유용 합니다. CD를 지정 하면 운영 체제에서 이동식 디스크의 이미지를 페이지 파일로 복사한 다음 로드 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **시스템** 속성 페이지를 클릭 합니다.

1. 다음 속성 중 하나를 수정 합니다.

   - **CD에서 스왑 실행**

   - **네트워크에서 스왑 실행**

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A> 속성을 참조하십시오.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
