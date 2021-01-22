---
description: 바인딩 지연 로드 된 가져오기에 대 한 자세한 정보
title: 바인딩 지연 로드 된 가져오기
ms.date: 01/19/2021
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.openlocfilehash: 49d321a30eeb3ab12ec832fb86a662f2035e1e3a
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98666942"
---
# <a name="bind-delay-loaded-imports"></a>바인딩 지연 로드 된 가져오기

기본 링커 동작은 지연 로드 된 DLL에 대해 바인딩 가능한 IAT (가져오기 주소 테이블)를 만드는 것입니다. DLL이 바인딩된 경우 도우미 함수는 `GetProcAddress` 참조 되는 각 가져오기에 대해를 호출 하는 대신 바인딩된 정보를 사용 하려고 합니다. 타임 스탬프 또는 기본 설정 주소가 로드 된 DLL의 타임 스탬프 또는 기본 설정 주소와 일치 하지 않는 경우 도우미 함수는 바인딩된 가져오기 주소 테이블이 최신이 아닌 것으로 가정 합니다. 이는 IAT가 없는 것 처럼 진행 됩니다.

DLL의 지연 로드 된 가져오기를 바인딩하지 않으려는 경우 [`/delay:nobind`](delay-delay-load-import-settings.md) 링커 명령줄에를 지정 합니다. 링커에서는 바인딩된 가져오기 주소 테이블을 생성 하지 않으므로 이미지 파일의 공간이 절약 됩니다.

## <a name="see-also"></a>참고 항목

[링커의 지연 로드된 DLL 지원](linker-support-for-delay-loaded-dlls.md)
