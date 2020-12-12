---
description: 자세히 알아보기:/MANIFESTDEPENDENCY (매니페스트 종속성 지정)
title: /MANIFESTDEPENDENCY(매니페스트 종속성 지정)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
ms.openlocfilehash: 129dc84818b0bda9b2106c0d07dca5b605dc6f96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199169"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY(매니페스트 종속성 지정)

```
/MANIFESTDEPENDENCY:manifest_dependency
```

## <a name="remarks"></a>설명

/MANIFESTDEPENDENCY를 사용 하면 \<dependency> 매니페스트 파일의 섹션에 배치 되는 특성을 지정할 수 있습니다.

매니페스트 파일을 만드는 방법에 대 한 자세한 내용은 [/smanifest (Side-by-side 어셈블리 매니페스트 만들기)](manifest-create-side-by-side-assembly-manifest.md) 를 참조 하세요.

매니페스트 파일의 섹션에 대 한 자세한 내용은 \<dependency> [게시자 구성 파일](/windows/win32/SbsCs/publisher-configuration-files)을 참조 하세요.

/MANIFESTDEPENDENCY 정보는 다음 두 가지 방법 중 하나로 링커에 전달할 수 있습니다.

- /MANIFESTDEPENDENCY.를 사용 하는 명령줄 (또는 지시 파일)에서 직접

- [주석](../../preprocessor/comment-c-cpp.md) pragma를 통해.

다음 예제에서는 pragma를 통해 전달 되는/MANIFESTDEPENDENCY 주석을 보여 줍니다.

```cpp
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")
```

그러면 매니페스트 파일에 다음 항목이 생성 됩니다.

```xml
<dependency>
  <dependentAssembly>
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />
  </dependentAssembly>
</dependency>
```

동일한/MANIFESTDEPENDENCY 주석을 명령줄에서 다음과 같이 전달할 수 있습니다.

```cmd
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"
```

링커가/MANIFESTDEPENDENCY 주석을 수집 하 고 중복 된 항목을 제거한 다음 생성 된 XML 문자열을 매니페스트 파일에 추가 합니다.  링커가 충돌 하는 항목을 찾으면 매니페스트 파일이 손상 되 고 응용 프로그램이 시작 되지 않습니다 (오류 원인을 나타내는 항목이 이벤트 로그에 추가 될 수 있음).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **매니페스트 파일** 속성 페이지를 선택 합니다.

1. **추가 매니페스트 종속성** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
