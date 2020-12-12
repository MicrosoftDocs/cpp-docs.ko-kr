---
description: 자세히 알아보기:/LARGEADDRESSAWARE (대량 주소 처리)
title: /LARGEADDRESSAWARE(큰 주소 처리)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
ms.openlocfilehash: 72b2ba20b2ea2b91ecd234497c433bcdd9e9ee42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199573"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE(큰 주소 처리)

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>설명

/LARGEADDRESSAWARE 옵션은 응용 프로그램이 2gb를 초과 하는 주소를 처리할 수 있음을 링커에 지시 합니다. 64 비트 컴파일러에서이 옵션은 기본적으로 사용 하도록 설정 되어 있습니다. 32 비트 컴파일러에서/LARGEADDRESSAWARE: NO는 링커 줄에/LARGEADDRESSAWARE가 지정 되지 않은 경우 사용 하도록 설정 됩니다.

응용 프로그램이/LARGEADDRESSAWARE에 연결 된 경우 DUMPBIN [/헤더](headers.md) 는 해당 효과에 대 한 정보를 표시 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **시스템** 속성 페이지를 클릭 합니다.

1. **Large Addresses 사용** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
