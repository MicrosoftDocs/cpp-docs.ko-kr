---
title: 심각한 오류 C1305 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1305
dev_langs:
- C++
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90d73003d9f19eb41f9eb34cd47c7b90b1e6164f
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539875"
---
# <a name="fatal-error-c1305"></a>심각한 오류 C1305
'pgd_file' 프로필 데이터베이스는 다른 아키텍처용입니다.  
  
 다른 플랫폼에 전달 된에 대 한 /ltcg: pginstrument 작업에서 생성 된.pgd 파일로 [/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md) 합니다. [프로필 기반 최적화](../../build/reference/profile-guided-optimizations.md) x86 및 x64 플랫폼에 사용할 수 있습니다. 그러나 단일 플랫폼에 대 한 /ltcg: pginstrument 작업과 생성 된.pgd 파일을 올바르지 다른 플랫폼에 대 한 /ltcg: pgoptimize 입력으로 합니다.  
  
 이 오류를 해결 하려면만 동일한 플랫폼에서 /ltcg: pgoptimize /ltcg: pginstrument를 사용 하 여 만든.pgd 파일을 전달 합니다.