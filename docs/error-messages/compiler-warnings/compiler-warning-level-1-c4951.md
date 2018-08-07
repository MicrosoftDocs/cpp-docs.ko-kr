---
title: 컴파일러 경고 (수준 1) C4951 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4951
dev_langs:
- C++
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3ebf012338bdf6b90cc943e754056335c6751a4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290467"
---
# <a name="compiler-warning-level-1-c4951"></a>컴파일러 경고(수준 1) C4951
프로필 데이터가 수집된 이후 'function'이 편집되었습니다. 함수 프로필 데이터가 사용되지 않습니다.  
  
 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)에 대한 입력 모듈에서 함수가 편집되어 이제 프로필 데이터가 유효하지 않습니다. **/LTCG:PGINSTRUMENT** 후에 입력 모듈이 다시 컴파일되었으며,***/LTCG:PGINSTRUMENT***작업 시 모듈에 있던 것과 다른 제어 흐름을 가진 함수( **function** )가 있습니다.  
  
 이 경고는 정보 제공용입니다. 이 경고를 해결하려면 **/LTCG:PGINSTRUMENT**를 실행하고 모든 테스트 실행을 다시 실행한 다음 **/LTCG:PGOPTIMIZE**를 실행합니다.  
  
 **/LTCG:PGOPTIMIZE** 를 사용한 경우 이 경고는 오류로 대체됩니다.