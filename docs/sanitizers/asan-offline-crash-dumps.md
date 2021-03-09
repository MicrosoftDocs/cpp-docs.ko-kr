---
title: AddressSanitizer 클라우드 또는 분산 테스트
description: Visual Studio 및 Azure 용으로 확장 된 AddressSanitizer 기능
ms.date: 03/02/2021
helpviewer_keywords:
- AddressSanitizer cloud or distributed testing
ms.openlocfilehash: 53bbb1ca04a5c4636914591cf10bfcc6bf275d42
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471328"
---
# <a name="addresssanitizer-cloud-or-distributed-testing"></a>AddressSanitizer 클라우드 또는 분산 테스트

AddressSanitizer 오류가 발생 하는 시기와 위치를 디버그할 필요가 없습니다. 오류가 발생할 때 AddressSanitizer 특정 컨텍스트를 모두 저장 하는 크래시 덤프를 만들도록 런타임을 구성 합니다. 그런 다음 디버깅을 위해 다른 PC로 크래시 덤프를 보냅니다. 클라우드 또는 분산 테스트에서 AddressSanitizer를 실행 하는 경우 오프 라인 디버깅은 중요 한 절약할 수 있습니다. 오류가 발생 하는 테스트 또는 프로덕션 인프라에서 덤프를 만들고 나중에 개발자 PC에서 디버그할 수 있습니다.

Visual Studio 디버거는 정확히 진단 된 AddressSanitizer 오류를 제공 합니다. 테스트를 다시 실행 하거나, 큰 데이터 집합을 복사 하거나, 손실 된 데이터를 검색 하거나, 오프 라인으로 전환 된 테스트 컴퓨터를 찾을 필요 없이 이러한 버그를 볼 수 있습니다. 크래시 덤프를 로드 하기만 하면 됩니다.

크래시 덤프는 다음 환경 변수를 설정 하 여 AddressSanitizer 오류가 발생할 때 생성 됩니다.

`set ASAN_SAVE_DUMPS=MyFileName.dmp`

> [!NOTE]
> *`.dmp`* Visual Studio 명명 규칙을 따르려면 파일 이름에 접미사가 있어야 합니다.

이 [덤프 파일](/previous-versions/windows/desktop/proc_snap/export-a-process-snapshot-to-a-file) 은 나중에 다른 컴퓨터에서 Visual Studio를 사용 하 여 표시할 수 있습니다.

Visual Studio는 원래 소스 코드의 컨텍스트에서 오류 정보를 표시할 수 있습니다. 이렇게 하려면 Visual Studio에서 [디버깅 기호와](/windows/win32/dxtecharts/debugging-with-symbols) [인덱싱된 소스 코드가](/windows-hardware/drivers/debugger/source-indexing)필요 합니다. 최상의 디버깅 환경을 위해 해당 이진 파일을 생성 하는 데 사용 되는 EXE, PDB 및 소스 코드가 일치 해야 합니다.

소스 및 기호를 저장 하는 방법에 대 한 자세한 내용은 [소스 및 기호](#source) 섹션을 참조 하세요. 구현 세부 정보 및 세분화 컨트롤에 대 한 자세한 내용은 [디버거 통합](asan-debugger-integration.md)을 참조 하세요.

## <a name="example---build-test-and-analyze"></a>예제-빌드, 테스트 및 분석

A, B, C의 세 가지 컴퓨터를 생각해 보세요. 빌드는 B 컴퓨터에서 수행 되 고, 테스트는 컴퓨터 C에서 실행 되며, 컴퓨터 A에서 오류를 분석 합니다. 소스 코드의 소스 줄과 열 번호에 대해 오류가 보고 됩니다. [소스 코드의 정확한 버전](#source)을 사용 하 여 생성 된 PDB 파일에서 기호 집합과 함께 호출 스택을 볼 수 있습니다.

다음 단계는 .dmp 파일을 만들고 오프 라인으로 해당 AddressSanitizer 덤프 파일을 보는 로컬 또는 분산 시나리오에 대 한 것입니다.

### <a name="produce-a-dmp-locally"></a>로컬에서 .dmp 생성

- 빌드
- 실행 파일 테스트
- 생성 된 .dmp 파일을 빌드 디렉터리에 복사 합니다.
- 동일한 디렉터리에서 쌍을 이루는 .pdb를 사용 하 여 .dmp 파일을 엽니다.

### <a name="produce-a-dmp-on-a-distributed-system"></a>분산 시스템에서 dmp 생성

- [원본 인덱싱 데이터 블록](/windows/win32/debug/source-server-and-source-indexing) 에 대 한 PDB 빌드 및 [사후 처리](#source)
- (.Exe, .pdb)의 원자성 쌍을 테스트 컴퓨터에 복사 하 고 테스트를 실행 합니다.
- 버그 보고 데이터베이스에 (.pdb, .dmp)의 원자성 쌍을 씁니다.
- Visual Studio에서 동일한 디렉터리에 쌍을 이루는 .pdb를 사용 하 여 .dmp 파일이 열립니다.

> [!NOTE]
> 분석에 사용 하는 Visual Studio 2019 컴퓨터는 GitHub 또는 인덱싱된 원본이 저장 된 내부에 액세스할 수 있어야 합니다 *`\\Machine\share`* .

## <a name="view-addresssanitizer-dmp-files"></a>AddressSanitizer 파일 보기

1. 디버거 IDE에서 PDB 및 소스 파일을 찾을 수 있는지 확인 합니다.

1. Visual Studio를 열고 **코드를 제외** 하 고 계속을 선택 합니다. 그런 다음 **파일**  >  **열기**  >  **파일** 을 선택 하 여 파일 열기 대화 상자를 엽니다. 파일 이름 접미사가 .dmp 인지 확인 합니다 **.**

   :::image type="content" source="./media/asan-open-crash-dump-file.png" alt-text="Visual Studio에서 파일 열기 메뉴의 스크린샷":::

   여기에 표시 된 화면에는 IDE에서 기호 및 소스에 액세스할 수 있도록 하는 단계가 하나 더 필요 합니다.

1. 기호 경로를 설정 하 고 **네이티브만 사용 하 여 디버그** 를 선택 합니다.

   :::image type="content" source="./media/asan-dump-file-open.png" alt-text="Visual Studio에서 미니 덤프 요약 표시의 스크린샷":::

이 스크린샷은 원본 및 AddressSanitizer 메타 데이터가 로드 된 최종 로드 된 덤프 파일을 보여 줍니다.

:::image type="content" source="./media/asan-view-crash-metadata.png" alt-text="소스 파일 및 AddressSanitizer 메타 데이터를 보여 주는 디버거의 스크린샷":::

## <a name="source-and-symbols"></a><a name="source"></a> 소스 및 기호

원본 서버를 사용 하면 클라이언트에서 응용 프로그램을 빌드하는 데 사용 되는 원본 파일의 **정확한 버전** 을 검색할 수 있습니다. 실행 파일 또는 DLL에 대 한 소스 코드는 시간이 지남에 따라 변경 될 수 있으며 버전 간에 변경 될 수 있습니다. 이를 사용 하 여 특정 버전의 응용 프로그램을 빌드한 동일한 소스 코드를 살펴볼 수 있습니다.

PDB 파일을 사용 하 여 EXE를 디버그 하는 동안 디버거는 포함 된 소스 서버 데이터 블록을 사용 하 여 소스 제어에서 적절 한 파일을 검색할 수 있습니다. 컴파일러 옵션에 의해 자동으로 PDB에 배치 되는 정규화 된 이름에 매핑되는 파일을 로드 합니다 **`/Zi`** .

원본 서버를 사용 하려면를 사용 하 여 *`pdbstr.exe`* `srcsrv` PDB 파일에 데이터 블록을 쓰도록 응용 프로그램이 "원본 인덱싱" 이어야 합니다. 자세한 내용은 [원본 서버 및 원본 인덱싱](/windows/win32/debug/source-server-and-source-indexing)의 데이터 블록 섹션을 참조 하세요. [소스를 인덱싱하고 기호를 게시 하는 단계](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) 와 [디버거의 기호 및 소스 코드를 지정 하는 방법을](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger) 찾을 수 있습니다.

외부 설명서는 다음을 참조 하세요.

- [Git를 사용 하 여 원본 인덱싱](https://gist.github.com/baldurk/c6feb31b0305125c6d1a)
- [디버깅을 용이 하 게 하는 가이드](https://www.codeproject.com/articles/115125/source-indexing-and-symbol-servers-a-guide-to-easi)
- [원본 인덱싱이 과도 한 우수성](https://randomascii.wordpress.com/2011/11/11/source-indexing-is-underused-awesomeness/)

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
