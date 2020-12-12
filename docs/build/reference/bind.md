---
description: 다음에 대 한 자세한 정보:/CBIND
title: /BIND
ms.date: 11/04/2016
f1_keywords:
- /bind
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
ms.openlocfilehash: 87ea0265555991fca019760feec4395692c074ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187145"
---
# <a name="bind"></a>/BIND

```
/BIND[:PATH=path]
```

## <a name="remarks"></a>설명

이 옵션은 실행 파일 또는 DLL에 대 한 가져오기 주소 테이블의 진입점 주소를 설정 합니다. 프로그램의 로드 시간을 줄이려면이 옵션을 사용 합니다.

EDITBIN 명령줄의 *files* 인수에서 프로그램의 실행 파일 및 dll을 지정 합니다. /바인딩에 대 한 선택적 *경로* 인수는 지정 된 파일에 사용 되는 dll의 위치를 지정 합니다. 여러 디렉터리를 세미콜론 (**;**)으로 구분 합니다. *Path* 를 지정 하지 않으면 EDITBIN은 path 환경 변수에 지정 된 디렉터리를 검색 합니다. *Path* 를 지정 하면 EDITBIN은 경로 변수를 무시 합니다.

기본적으로 프로그램 로더는 프로그램을 로드할 때 진입점의 주소를 설정 합니다. Dll의 수와 프로그램에서 참조 되는 진입점의 수에 따라이 프로세스에 걸리는 시간이 달라 집니다. 프로그램이/CBIND로 수정 되었으며 실행 파일 및 해당 Dll의 기본 주소가 이미 로드 된 Dll과 충돌 하지 않는 경우 운영 체제에서 이러한 주소를 설정할 필요가 없습니다. 파일의 기반이 잘못 된 상황에서 운영 체제는 프로그램의 Dll을 재배치 하 고 진입점 주소를 다시 계산 하 여 프로그램의 로드 시간에 추가 합니다.

## <a name="see-also"></a>참고 항목

[EDITBIN 옵션](editbin-options.md)
