---
description: '자세한 정보: 라이브러리 관리'
title: 라이브러리 관리
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLibrarianTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLibrarianTool.AdditionalDependencies
- VC.Project.VCLibrarianTool.RemoveObjects
- VC.Project.VCLibrarianTool.LibraryPaths
- VC.Project.VCLibrarianTool.OutputFile
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryNames
- VC.Project.VCLibrarianTool.AdditionalLibraryDirectories
- VC.Project.VCLibrarianTool.ListContentsFile
- VC.Project.VCLibrarianTool.ListContents
- VC.Project.VCLibrarianTool.SubSystemVersion
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryName
- VC.Project.VCLibrarianTool.SubSystem
helpviewer_keywords:
- /LIBPATH library manager option
- OUT library manager option
- CONVERT library manager option
- LIBPATH library manager option
- /LIST library manager option
- object files, building and modifying
- -LINK50COMPAT library manager option
- REMOVE library manager option
- SUBSYSTEM library manager option
- /LINK50COMPAT library manager option
- /OUT library manager option
- LIB [C++], managing COFF libraries
- -CONVERT library manager option
- LINK50COMPAT library manager option
- -OUT library manager option
- -REMOVE library manager option
- -LIST library manager option
- /SUBSYSTEM library manager option
- -SUBSYSTEM library manager option
- /REMOVE library manager option
- -LIBPATH library manager option
- object files
- LIST library manager option
- /CONVERT library manager option
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
ms.openlocfilehash: f862dfd460bb51cdf6e855c87b08b7426a5642d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199131"
---
# <a name="managing-a-library"></a>라이브러리 관리

LIB의 기본 모드는 COFF 개체의 라이브러리를 작성 하거나 수정 하는 것입니다. /EXTRACT (개체를 파일에 복사) 또는/DEF (가져오기 라이브러리를 빌드하기 위해)를 지정 하지 않으면 LIB가이 모드에서 실행 됩니다.

개체 및/또는 라이브러리에서 라이브러리를 빌드하려면 다음 구문을 사용 합니다.

```
LIB [options...] files...
```

이 명령은 하나 이상의 입력 *파일* 에서 라이브러리를 만듭니다. *파일* 은 coff 개체 파일, 32 비트 OMF 개체 파일 또는 기존 coff 라이브러리 일 수 있습니다. LIB는 지정 된 파일의 모든 개체를 포함 하는 라이브러리를 하나 만듭니다. 입력 파일이 32 비트 OMF 개체 파일인 경우 라이브러리를 빌드하기 전에 LIB에서 COFF로 변환 합니다. LIB는 16 비트 버전의 LIB에서 만든 라이브러리에 있는 32 비트 OMF 개체를 받아들일 수 없습니다. 먼저 16 비트 LIB를 사용 하 여 개체를 추출 해야 합니다. 그런 다음 추출 된 개체 파일을 32 비트 LIB의 입력으로 사용할 수 있습니다.

기본적으로 LIB는 첫 번째 개체 또는 라이브러리 파일의 기본 이름 및 확장명 .lib를 사용 하 여 출력 파일의 이름을로 사용 합니다. 출력 파일은 현재 디렉터리에 저장 됩니다. 동일한 이름을 가진 파일이 이미 있는 경우에는 출력 파일이 기존 파일을 대체 합니다. 기존 라이브러리를 유지 하려면/OUT 옵션을 사용 하 여 출력 파일의 이름을 지정 합니다.

라이브러리를 작성 하 고 수정 하는 데 적용 되는 옵션은 다음과 같습니다.

**/Libpath:** *dir*<br/>
환경 라이브러리 경로를 재정의합니다. 자세한 내용은 [/LIBPATH](libpath-additional-libpath.md) 링크 옵션에 대 한 설명을 참조 하세요.

**/LIST**<br/>
출력 라이브러리에 대 한 정보를 표준 출력에 표시 합니다. 출력을 파일로 리디렉션할 수 있습니다. /LIST를 사용 하 여 기존 라이브러리를 수정 하지 않고 콘텐츠를 확인할 수 있습니다.

**/Name:** *filename*<br/>
가져오기 라이브러리를 빌드할 때 가져오기 라이브러리를 빌드할 DLL의 이름을 지정 합니다.

**/NODEFAULTLIB**<br/>
외부 참조를 확인할 때 검색 하는 라이브러리 목록에서 하나 이상의 기본 라이브러리를 제거 합니다. 자세한 내용은 [/nodefaultlib](nodefaultlib-ignore-libraries.md) 를 참조 하세요.

**/Out:** *filename*<br/>
기본 출력 파일 이름을 재정의 합니다. 기본적으로 출력 라이브러리는 현재 디렉터리에 생성 되 고, 첫 번째 라이브러리 또는 개체 파일의 기본 이름이 명령줄 및 확장명 .lib로 생성 됩니다.

**/Remove:** *개체*<br/>
지정 된 *개체* 를 출력 라이브러리에서 생략 합니다. LIB는 모든 개체 (개체 파일 또는 라이브러리)를 결합 하 여 출력 라이브러리를 만든 다음/REMOVE.를 사용 하 여 지정 된 개체를 삭제 합니다.

**/SUBSYSTEM:**{**CONSOLE** &#124; **EFI_APPLICATION** &#124; **EFI_BOOT_SERVICE_DRIVER** &#124; **EFI_ROM** &#124; **EFI_RUNTIME_DRIVER** &#124; **NATIVE** &#124; **POSIX** &#124; **WINDOWS** &#124; **WINDOWSCE**} [, # [. # #]]<br/>
운영 체제에서 출력 라이브러리에 연결 하 여 만든 프로그램을 실행 하는 방법을 알려 줍니다. 자세한 내용은 LINK [/SUBSYSTEM](subsystem-specify-subsystem.md) 옵션에 대 한 설명을 참조 하세요.

명령줄에 지정 된 LIB 옵션은 대/소문자를 구분 하지 않습니다.

LIB를 사용 하 여 다음과 같은 라이브러리 관리 작업을 수행할 수 있습니다.

- 라이브러리에 개체를 추가 하려면 기존 라이브러리의 파일 이름과 새 개체의 이름을 지정 합니다.

- 라이브러리를 결합 하려면 라이브러리 파일 이름을 지정 합니다. 단일 LIB 명령을 사용 하 여 개체를 추가 하 고 라이브러리를 결합할 수 있습니다.

- 라이브러리 멤버를 새 개체로 바꾸려면 바꾸려는 멤버 개체가 포함 된 라이브러리와 새 개체 (또는이를 포함 하는 라이브러리)의 파일 이름을 지정 합니다. 동일한 이름을 가진 개체가 둘 이상의 입력 파일에 있는 경우 LIB는 LIB 명령에 지정 된 마지막 개체를 출력 라이브러리에 넣습니다. 라이브러리 멤버를 바꿀 때 이전 개체를 포함 하는 라이브러리 뒤에 새 개체 또는 라이브러리를 지정 해야 합니다.

- 라이브러리에서 멤버를 삭제 하려면/REMOVE 옵션을 사용 합니다. LIB는 명령줄 순서에 관계 없이 모든 입력 개체를 결합 한 후/REMOVE의 모든 사양을 처리 합니다.

> [!NOTE]
> 동일한 단계에서 멤버를 삭제 하 고 파일에 추출할 수 없습니다. 먼저/EXTRACT를 사용 하 여 멤버 개체를 추출한 다음/REMOVE.를 사용 하 여 LIB를 다시 실행 해야 합니다. 이 동작은 다른 Microsoft 제품에서 제공 되는 16 비트 LIB (OMF 라이브러리의 경우)와는 다릅니다.

## <a name="see-also"></a>참고 항목

[LIB 참조](lib-reference.md)
