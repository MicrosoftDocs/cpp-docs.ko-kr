---
title: pgosweep
description: 프로필 기반 최적화에서 활용할 수 있도록 pgosweep 명령을 사용해 PGC 파일에 프로필 데이터를 씁니다.
ms.date: 10/23/2020
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.openlocfilehash: be96d0f092ff65867c304ddf5eb41c0754f6e4be
ms.sourcegitcommit: bf54b407169900bb668c85a67b31dbc0f069fe65
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92497183"
---
# <a name="pgosweep"></a>pgosweep

프로필 기반 최적화에서 PGC 파일에 실행 중인 프로그램의 모든 프로필 데이터를 쓰는 데 사용합니다.

## <a name="syntax"></a>Syntax

> **`pgosweep`** [ *options* ] *image* *pgcfile*

### <a name="parameters"></a>매개 변수

*options*\
(선택 사항) *options* 의 유효한 값은 다음과 같습니다.

- **`/?`** 또는 **`/help`** 도움말 메시지를 표시합니다.

- **`/reset`** 스윕 후 개수를 0으로 초기화합니다. 이 동작은 기본값입니다.

- **`/pid:n`** 지정된 PID만 스윕하며, 여기서 *n* 은 PID 번호입니다.

- **`/wait`** 개수를 수집하기 전 지정된 PID가 종료될 때까지 대기합니다.

- **`/onlyzero`** PGC 파일이 아닌 0인 개수만 저장합니다.

- **`/pause`** 시스템의 개수 수집을 일시 중지합니다.

- **`/resume`** 시스템의 개수 수집을 다시 시작합니다.

- **`/noreset`** 런타임 데이터 구조에서 개수를 유지합니다.

*image*\
[`/GENPROFILE`](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [`/FASTGENPROFILE`](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) 또는 [`/LTCG:PGINSTRUMENT`](reference/ltcg-link-time-code-generation.md) 옵션을 사용하여 만든 EXE 또는 DLL 파일의 전체 경로입니다.

*pgcfile*\
이 명령이 데이터 개수를 기록하는 PGC 파일입니다.

## <a name="remarks"></a>설명

**`pgosweep`** 명령은 [`/GENPROFILE`, `/FASTGENPROFILE`](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), 또는 이제 더는 사용되지 않는 [`/LTCG:PGINSTRUMENT`](reference/ltcg-link-time-code-generation.md) 옵션을 사용하여 빌드한 프로그램에서 작동합니다. 이 명령은 실행 중인 프로그램을 중단하고 새 PGC 파일에 프로필 데이터를 기록합니다. 기본적으로 이 명령은 각 쓰기 작업 후에 개수를 다시 설정합니다. **`/noreset`** 옵션을 지정하면 이 명령이 값을 기록하지만 실행 중인 프로그램에서 값을 초기화하지 않습니다. 이 옵션을 사용하는 경우 나중에 프로필 데이터를 검색할 때 중복 데이터가 제공됩니다.

**`pgosweep`** 의 다른 용도는 애플리케이션의 정상 작업에 관한 프로필 정보만 검색하는 것입니다. 예를 들어 애플리케이션을 시작하고 해당 파일을 삭제한 후 바로 **`pgosweep`** 를 실행할 수 있습니다. 이 명령은 시작 비용과 관련된 프로필 데이터를 제거합니다. 그런 다음 애플리케이션을 종료하기 전에 **`pgosweep`** 를 실행할 수 있습니다. 이제 수집된 데이터에는 사용자가 프로그램을 조작할 수 있는 때부터의 프로필 정보만 포함됩니다.

*pcgfile* 매개 면수를 사용하여 PCG 파일의 이름을 지정할ㅇ 때 표준 형식인 *`appname!n.pgc`* 를 사용할 수 있습니다. *n* 은 각 파일에 대해 증가하는 숫자 값을 나타냅니다. 이 형식을 사용하면 컴파일러는 자동으로 **`/LTCG /USEPROFILE`** 또는 **`/LTCG:PGO`** 단계에서 이 데이터를 찾습니다. 표준 형식을 사용하지 않는 경우에는 [`pgomgr`](pgomgr.md)을 사용하여 PGC 파일을 병합해야 합니다.

> [!NOTE]
> 이 도구는 Visual Studio 개발자 명령 프롬프트에서만 시작할 수 있습니다. 시스템 명령 프롬프트 또는 파일 탐색기에서는 시작할 수 없습니다.

실행 파일 내에서 프로필 데이터를 캡처하는 자세한 방법은 [`PgoAutoSweep`](pgoautosweep.md)를 참조하세요.

## <a name="example"></a>예제

이 예제 명령에서 **`pgosweep`** 은 *`myapp.exe`* 의 현재 프로필 정보를 *`myapp!1.pgc`* 에 기록합니다.

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>추가 정보

[프로필 기반 최적화](profile-guided-optimizations.md)\
[PgoAutoSweep](pgoautosweep.md)
