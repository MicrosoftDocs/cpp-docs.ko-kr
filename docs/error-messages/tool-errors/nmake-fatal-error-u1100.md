---
title: "NMAKE 심각한 오류 U1100 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1100
dev_langs:
- C++
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7c4a42e47a29775bb53fdc0fd2f25c7bdc252f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE 심각한 오류 U1100
매크로 '매크로 이름' 'rule' 일괄 처리 규칙의 컨텍스트에서 올바르지 않습니다.  
  
 NMAKE는 배치 모드 규칙의 명령 블록이 $<가 아닌 특수한 파일 매크로를 직접적 또는 간접적으로 참조할 때 이 오류를 생성합니다.  
  
 배치 모드 규칙에는 $< 매크로만 사용할 수 있습니다.