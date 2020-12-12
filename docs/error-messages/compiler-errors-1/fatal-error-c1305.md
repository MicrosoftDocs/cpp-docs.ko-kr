---
description: '자세한 정보: 심각한 오류 C1305'
title: 심각한 오류 C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 100046d5ad7c6fa943358063d3d3cb21ffa00e5d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267900"
---
# <a name="fatal-error-c1305"></a>심각한 오류 C1305

' pgd_file ' 프로필 데이터베이스는 다른 아키텍처용입니다.

다른 플랫폼에 대 한/LTCG: PGINSTRUMENT 작업에서 생성 된 .pgd 파일이 [/ltcg: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) 에 전달 되었습니다. [프로필 기반 최적화](../../build/profile-guided-optimizations.md) 는 x86 및 x64 플랫폼에서 사용할 수 있습니다. 그러나 한 플랫폼에 대해/LTCG: PGINSTRUMENT 작업을 사용 하 여 생성 된 .pgd 파일은 다른 플랫폼에 대 한/LTCG: PGOPTIMIZE에 대 한 입력으로 유효 하지 않습니다.

이 오류를 해결 하려면/LTCG: PGINSTRUMENT 사용 하 여 만든 .pgd 파일만 동일한 플랫폼의/LTCG: PGOPTIMIZE에 전달 합니다.
