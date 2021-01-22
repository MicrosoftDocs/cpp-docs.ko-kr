---
description: '자세한 정보: 지연 로드 된 가져오기 덤프'
title: 덤프 지연 로드 된 가져오기
ms.date: 01/19/2021
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.openlocfilehash: 6a0fec0b10bc29ea919195302334a25f71de0abd
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98666916"
---
# <a name="dump-delay-loaded-imports"></a>덤프 지연 로드 된 가져오기

지연 로드 된 가져오기는를 사용 하 여 덤프할 수 있습니다 [`dumpbin /imports`](imports-dumpbin.md) . 이러한 가져오기는 표준 가져오기와 약간 다른 정보를 표시 합니다. 이러한 항목은 목록의 고유한 섹션으로 분리 `/imports` 되며 명시적으로 지연 로드 된 가져오기로 레이블이 지정 됩니다. 이미지에 언로드 정보가 있는 경우 해당 정보가 표시 됩니다. 바인딩 정보가 있는 경우 대상 DLL의 시간 및 날짜 스탬프가 가져오기의 바인딩된 주소와 함께 표시 됩니다.

## <a name="see-also"></a>참고 항목

[링커의 지연 로드된 DLL 지원](linker-support-for-delay-loaded-dlls.md)
