---
description: '다음에 대 한 자세한 정보: NMAKE 경고 U4004'
title: NMAKE 경고 U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: 44326bfb6a69b583967163054b4510bf5c50d6bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345292"
---
# <a name="nmake-warning-u4004"></a>NMAKE 경고 U4004

' targetname ' 대상에 대 한 규칙이 너무 많습니다.

단일 콜론 (**:**)을 구분 기호로 사용 하 여 지정 된 대상에 대해 둘 이상의 설명 블록이 지정 되었습니다. NMAKE는 첫 번째 설명 블록의 명령을 실행 하 고 이후 블록을 무시 합니다.

여러 종속성에서 동일한 대상을 지정 하려면 `::` 각 종속성 줄에서 구분 기호로 이중 콜론 ()을 사용 합니다.
