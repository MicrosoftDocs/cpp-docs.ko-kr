---
title: "심각한 오류 C1305 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1305
dev_langs:
- C++
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b32f9e7555ce905323fd6074d35f1876cd999edd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1305"></a>심각한 오류 C1305
'pgd_file' 프로필 데이터베이스는 다른 아키텍처용입니다.  
  
 다른 플랫폼에 전달 된에 대 한 /ltcg: pginstrument 작업에서 생성 된.pgd 파일 [/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md) 합니다. [프로필 기반 최적화](../../build/reference/profile-guided-optimizations.md) x86에 사용할 수 있는 및 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 플랫폼입니다. 그러나.pgd 파일을 생성 한 플랫폼에 대 한 /ltcg: pginstrument 작업과 유효 하지 다른 플랫폼에 대 한 /ltcg: pgoptimize는 입력으로 합니다.  
  
 이 오류를 해결 하려면만 /ltcg: pginstrument 동일한 플랫폼에서 /ltcg: pgoptimize 사용 하 여 만든.pgd 파일을 전달 합니다.