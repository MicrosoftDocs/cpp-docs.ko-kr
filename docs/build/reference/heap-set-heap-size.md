---
description: 다음에 대 한 자세한 정보:/S힙 (힙 크기 설정)
title: /HEAP(힙 크기 설정)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: 9831180925d5d669c799982d021d75ea31a2dae5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191669"
---
# <a name="heap-set-heap-size"></a>/HEAP(힙 크기 설정)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>설명

/SV힙 옵션은 힙의 크기 (바이트)를 설정 합니다. 이 옵션은 .exe 파일을 빌드할 때만 사용 됩니다.

*Reserve* 인수는 가상 메모리의 총 힙 할당을 지정 합니다. 기본 힙 크기는 1mb입니다. 링커에서는 지정 된 값을 가장 가까운 4 바이트로 반올림 합니다.

선택적 `commit` 인수는 한 번에 할당할 실제 메모리의 양을 지정 합니다. 커밋된 가상 메모리를 설정 하면 페이징 파일에 공간이 예약 됩니다. `commit`값이 클수록 응용 프로그램에 더 많은 힙 공간이 필요할 때 시간이 절약 되지만 메모리 요구 사항과 시작 시간이 늘어날 수 있습니다.

*예약* 및 값을 `commit` 10 진수 또는 C 언어 표기법으로 지정 합니다.

이 기능은 [HEAPSIZE](heapsize.md)를 사용 하는 모듈 정의 파일을 통해서도 사용할 수 있습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **시스템** 속성 페이지를 클릭 합니다.

1. **힙 커밋 크기** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>를 확인합니다.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
