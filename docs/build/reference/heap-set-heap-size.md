---
title: /HEAP(힙 크기 설정)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: 500e1eca9385697829edca46e5e703a5238684a7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422374"
---
# <a name="heap-set-heap-size"></a>/HEAP(힙 크기 설정)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>설명

/HEAP 옵션 힙의 크기를 바이트 단위로 설정 합니다. 이 옵션은.exe 파일을 작성 하는 경우에 사용 합니다.

합니다 *예약할* 인수 가상 메모리의 총 힙 할당을 지정 합니다. 기본 힙 크기는 1MB입니다. 링커는 가장 가까운 4 바이트에 지정된 된 값으로 반올림합니다.

선택적 `commit` 인수 한 번에 할당할 실제 메모리 양을 지정 합니다. 커밋된 가상 메모리 페이징 파일에 예약 될 공간을 하면 됩니다. 더 높은 `commit` 값 응용 프로그램의 힙 공간이 더 필요 하지만 메모리 요구 사항 및 시작 시간 증가 하면 시간을 절약할 수 있습니다.

지정 된 *예약할* 및 `commit` 10 진수 또는 C 언어 표기법으로 값입니다.

에서도이 기능을 사용 하 여 모듈 정의 파일을 통해 사용할 수 있습니다 [HEAPSIZE](../../build/reference/heapsize.md)합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 참조 하세요 [Visual c + + 프로젝트 속성 설정](../../ide/working-with-project-properties.md)합니다.

1. 클릭 합니다 **링커** 폴더입니다.

1. 클릭 합니다 **시스템** 속성 페이지.

1. 수정 된 **힙 커밋 크기** 속성입니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>을 참조하십시오.

## <a name="see-also"></a>참고자료

[링커 옵션 설정](../../build/reference/setting-linker-options.md)<br/>
[링커 옵션](../../build/reference/linker-options.md)
