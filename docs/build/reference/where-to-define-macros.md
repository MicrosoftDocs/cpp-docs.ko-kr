---
description: '자세한 정보: 매크로를 정의 하는 위치'
title: 매크로를 정의할 위치
ms.date: 11/04/2016
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
ms.openlocfilehash: b5fc7d6e1fd8247816993929791bf734596d00e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259203"
---
# <a name="where-to-define-macros"></a>매크로를 정의할 위치

명령줄, 명령 파일, 메이크파일 또는 Tools.ini 파일에서 매크로를 정의 합니다.

메이크파일 또는 Tools.ini 파일에서 각 매크로 정의는 별도의 줄에 표시 되어야 하며 공백이 나 탭으로 시작할 수 없습니다. 등호 주위의 공백이 나 탭은 무시 됩니다. 모든 [문자열 문자](defining-an-nmake-macro.md) 는 주변 따옴표 및 포함 된 공백을 포함 하 여 리터럴입니다.

명령줄 또는 명령 파일에서 공백과 탭은 인수를 구분 하 고 등호를 묶을 수 없습니다. `string`에 공백이 나 탭이 있으면 문자열 자체 또는 전체 매크로를 큰따옴표 ("")로 묶습니다.

## <a name="see-also"></a>참고 항목

[NMAKE 매크로 정의](defining-an-nmake-macro.md)
