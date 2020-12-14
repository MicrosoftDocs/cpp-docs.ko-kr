---
description: '자세한 정보: 링크 출력'
title: LINK 출력
ms.date: 11/04/2016
helpviewer_keywords:
- mapfiles [C++]
- ILK files
- output files [C++], linker
- files [C++], LINK
- .ilk files
- LINK tool [C++], output
- import libraries [C++], creating
- executable files [C++], as linker output
- mapfiles [C++], LINK output
- linker [C++], output files
- DLLs [C++], as linker output
- LINK tool [C++], mapfile
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
ms.openlocfilehash: 18d14fda2702e588f69c8a613783087895827826
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190993"
---
# <a name="link-output"></a>LINK 출력

링크 출력에는 .exe 파일, Dll, mapfiles 및 메시지가 포함 됩니다.

## <a name="output-files"></a><a name="_core_output_files"></a> 출력 파일

링크의 기본 출력 파일은 .exe 파일입니다. [/Dll](dll-build-a-dll.md) 옵션을 지정 하면 LINK에서 .dll 파일을 빌드합니다. 출력 파일 이름 [(/out)](out-output-file-name.md) 옵션을 사용 하 여 출력 파일 이름을 제어할 수 있습니다.

증분 모드에서 링크는 프로그램의 이후 증분 빌드에 대 한 상태 정보를 저장 하는 .ilk 파일을 만듭니다. .Ilk 파일에 대 한 자세한 내용은 [.Ilk 파일](dot-ilk-files-as-linker-input.md)을 참조 하세요. 증분 링크에 대 한 자세한 내용은 증분 [링크 (/INCREMENTAL)](incremental-link-incrementally.md) 옵션을 참조 하십시오.

LINK가 내보내기 (일반적으로 DLL)를 포함 하는 프로그램을 만드는 경우 빌드에서 .exp 파일을 사용 하지 않으면 .lib 파일도 빌드됩니다. [/IMPLIB](implib-name-import-library.md) 옵션을 사용 하 여 가져오기 라이브러리 파일 이름을 제어할 수 있습니다.

[맵 파일 생성 (/map)](map-generate-mapfile.md) 옵션을 지정 하면 LINK에서 맵 파일을 만듭니다.

[디버그 정보 생성 (/debug)](debug-generate-debug-info.md) 옵션이 지정 된 경우 LINK에서는 프로그램에 대 한 디버깅 정보를 포함 하는 PDB를 만듭니다.

## <a name="other-output"></a><a name="_core_other_output"></a> 기타 출력

`link`다른 명령줄 입력 없이를 입력 하는 경우 링크에는 해당 옵션을 요약 하는 사용 문이 표시 됩니다.

링크를 사용 하면 저작권 및 버전 메시지가 표시 되 고, [/nologo (시작 배너 표시 안 함)](nologo-suppress-startup-banner-linker.md) 옵션을 사용 하지 않는 한 명령 파일 입력이 에코 됩니다.

[진행률 메시지 인쇄 (/verbose)](verbose-print-progress-messages.md) 옵션을 사용 하 여 빌드에 대 한 추가 정보를 표시할 수 있습니다.

.LNK *nnnn* 의 형식으로 문제 오류 및 경고 메시지를 연결 합니다. 이 오류 접두사 및 숫자 범위는 LIB, DUMPBIN 및 EDITBIN에도 사용 됩니다.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
