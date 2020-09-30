---
title: /IDLOUT(MIDL 출력 파일 이름 지정)
ms.date: 11/04/2016
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
ms.openlocfilehash: 8dc26a0564a979c918d1eb1eb85e63e9c73caba0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506935"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT(MIDL 출력 파일 이름 지정)

```
/IDLOUT:[path\]filename
```

## <a name="parameters"></a>매개 변수

*path*<br/>
절대 또는 상대 경로 지정입니다. 경로를 지정 하 여 .idl 파일의 위치에만 영향을 줍니다. 다른 모든 파일은 프로젝트 디렉터리에 배치 됩니다.

*filename*<br/>
MIDL 컴파일러에 의해 생성 된 .idl 파일의 이름을 지정 합니다. 파일 확장명을 가정 하지 않습니다. .idl 확장명을 원하는 경우 *파일 이름을*.idl로 지정 합니다.

## <a name="remarks"></a>설명

/IDLOUT 옵션은 .idl 파일의 이름과 확장명을 지정 합니다.

MIDL 컴파일러는 [module](../../windows/attributes/module-cpp.md) 특성을 포함 하는 프로젝트를 연결할 때 MSVC 링커에서 호출 합니다.

또한/IDLOUT는 MIDL 컴파일러와 연결 된 다른 출력 파일의 파일 이름을 지정 합니다.

- *파일 이름*.tlb

- *파일 이름*_p .c

- *파일 이름*_i .c

- *파일 이름*.h

*filename* 은/IDLOUT.에 전달 하는 매개 변수입니다. [/TLBOUT](tlbout-name-dot-tlb-file.md) 가 지정 된 경우 .tlb 파일은/TLBOUT *filename*에서 이름을 가져옵니다.

/IDLOUT 또는/TLBOUT를 모두 지정 하지 않으면 링커가 vc70, vc70, vc70_p, vc70_i 및 vc70을 만듭니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **포함 된 IDL** 속성 페이지를 클릭 합니다.

1. **병합 IDL 기본 파일 이름** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)<br/>
[/IGNOREIDL (특성을 MIDL로 처리 하지 않음)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (MIDL 명령줄 옵션 지정)](midl-specify-midl-command-line-options.md)<br/>
[특성을 사용하는 프로그램 빌드](../../windows/attributes/cpp-attributes-com-net.md)
