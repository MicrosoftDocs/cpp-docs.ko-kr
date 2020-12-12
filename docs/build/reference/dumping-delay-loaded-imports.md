---
description: '자세한 정보: 가져오기 Delay-Loaded 덤프'
title: 지연 로드된 가져오기 덤프
ms.date: 11/04/2016
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
ms.openlocfilehash: c57ff6bb4a3dce16b4cb1eb85fdffff4ef272396
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201081"
---
# <a name="dumping-delay-loaded-imports"></a>지연 로드된 가져오기 덤프

지연 로드 된 가져오기는 [dumpbin/imports](imports-dumpbin.md) 를 사용 하 여 덤프할 수 있으며 표준 가져오기와 약간 다른 정보를 표시 합니다. 이러한 항목은/imports 덤프의 자체 섹션으로 분리 되며, 지연 로드 된 가져오기로 명시적으로 레이블이 지정 됩니다. 이미지에 언로드 정보가 있는 경우 해당 정보가 표시 됩니다. 바인딩 정보가 있는 경우 대상 DLL의 시간/날짜 스탬프는 가져오기의 바인딩된 주소와 함께 기록 됩니다.

## <a name="see-also"></a>참고 항목

[Delay-Loaded Dll에 대 한 링커 지원](linker-support-for-delay-loaded-dlls.md)
