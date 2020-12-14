---
description: 자세히 알아보기:/PDBPATH
title: /PDBPATH
ms.date: 11/04/2016
f1_keywords:
- /pdbpath
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
ms.openlocfilehash: 41207d7cfce3d72ecb9517d9ad3af8bcd3f901d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226053"
---
# <a name="pdbpath"></a>/PDBPATH

```
/PDBPATH[:VERBOSE] filename
```

### <a name="parameters"></a>매개 변수

*filename*<br/>
일치 하는 .pdb 파일을 찾을 .dll 또는 .exe 파일의 이름입니다.

**: 자세한 정보 표시**<br/>
필드 .Pdb 파일을 찾으려고 시도한 모든 디렉터리를 보고 합니다.

## <a name="remarks"></a>설명

/PDBPATH는 디버거가 .pdb 파일을 검색 하는 것과 동일한 경로를 따라 컴퓨터를 검색 하 고 .pdb 파일이 *filename* 에 지정 된 파일에 해당 하는 경우이를 보고 합니다.

Visual Studio 디버거를 사용 하는 경우 디버거가 디버그 중인 다른 버전의 파일에 .pdb 파일을 사용 하 고 있기 때문에 문제가 발생할 수 있습니다.

/PDBPATH는 다음 경로를 따라 .pdb 파일을 검색 합니다.

- 실행 파일이 있는 위치를 확인 합니다.

- 실행 파일에 기록 된 PDB의 위치를 확인 합니다. 일반적으로 이미지가 연결 된 시점의 위치입니다.

- Visual Studio IDE에서 구성 된 검색 경로를 따라 확인 합니다.

- _NT_SYMBOL_PATH 및 _NT_ALT_SYMBOL_PATH 환경 변수의 경로를 따라 확인 합니다.

- Windows 디렉터리를 확인 합니다.

## <a name="see-also"></a>참고 항목

[DUMPBIN 옵션](dumpbin-options.md)<br/>
[/PDBALTPATH (대체 PDB 경로 사용)](pdbaltpath-use-alternate-pdb-path.md)
