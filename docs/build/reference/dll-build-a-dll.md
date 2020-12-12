---
description: 자세히 알아보기:/DLL (DLL 빌드)
title: /DLL(DLL 빌드)
ms.date: 11/04/2016
f1_keywords:
- /dll
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
ms.openlocfilehash: 42535fb15762e5c0f1691d5c28029c7368005f87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201406"
---
# <a name="dll-build-a-dll"></a>/DLL(DLL 빌드)

```
/DLL
```

## <a name="remarks"></a>설명

/DLL 옵션은 DLL을 기본 출력 파일로 작성 합니다. DLL에는 일반적으로 다른 프로그램에서 사용할 수 있는 내보내기가 포함 되어 있습니다. 내보내기를 지정 하는 방법에는 다음과 같은 세 가지가 있습니다. 권장 되는 사용 순서 대로 나열 됩니다.

1. 소스 코드의 [__declspec (dllexport)](../../cpp/dllexport-dllimport.md)

1. .Def 파일의 [EXPORTS](exports.md) 문

1. LINK 명령의 [/export](export-exports-a-function.md) 사양

프로그램은 둘 이상의 메서드를 사용할 수 있습니다.

DLL을 빌드하는 또 다른 방법은 **라이브러리** 모듈 정의 문을 사용 하는 것입니다. /BASE와/DLL 옵션은 모두 **LIBRARY** 문과 동일 합니다.

개발 환경에서이 옵션을 지정 하지 마십시오. 이 옵션은 명령줄 에서만 사용할 수 있습니다. 이 옵션은 응용 프로그램 마법사를 사용 하 여 DLL 프로젝트를 만들 때 설정 됩니다.

임시 단계에서 가져오기 라이브러리를 만드는 경우 .dll을 만들기 전에 .dll을 빌드할 때 동일한 개체 파일 집합을 전달 해야 합니다 .이 파일은 가져오기 라이브러리를 빌드할 때 전달 된 것과 같습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** 폴더를 클릭 합니다.

1. **일반** 속성 페이지를 클릭 합니다.

1. **구성 유형** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
