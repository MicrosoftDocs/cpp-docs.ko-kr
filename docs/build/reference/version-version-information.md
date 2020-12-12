---
description: 자세히 알아보기:/VERSION (버전 정보)
title: /VERSION(버전 정보)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
ms.openlocfilehash: 7c6a27e4829c4acf66db2887e01a147aceb1c5d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176368"
---
# <a name="version-version-information"></a>/VERSION(버전 정보)

```
/VERSION:major[.minor]
```

## <a name="arguments"></a>인수

*주* 및 *부*<br/>
.Exe 또는 .dll 파일의 헤더에 원하는 버전 번호를 표시 합니다.

## <a name="remarks"></a>설명

/VERSION 옵션은 .exe 또는 .dll 파일의 헤더에 버전 번호를 삽입 하도록 링커에 지시 합니다. 옵션 헤더 값의 이미지 버전 필드를 확인 하려면 DUMPBIN [/HEADERS](headers.md) 를 사용 합니다.

*주* 및 *부* 인수는 0에서 65535 사이의 10 진수입니다. 기본값은 버전 0.0입니다.

/VERSION으로 지정된 정보는 파일 탐색기에서 해당 속성을 볼 때 애플리케이션에 대해 표시되는 버전 정보에 영향을 주지 않습니다. 해당 버전 정보는 응용 프로그램을 빌드하는 데 사용 되는 리소스 파일에서 가져옵니다. 자세한 내용은 [버전 정보 편집기](../../windows/version-information-editor.md) 를 참조 하십시오.

[버전 모듈 정의](version-c-cpp.md) 문을 사용 하 여 버전 번호를 삽입할 수도 있습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **일반** 속성 페이지를 클릭 합니다.

1. **Version** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
