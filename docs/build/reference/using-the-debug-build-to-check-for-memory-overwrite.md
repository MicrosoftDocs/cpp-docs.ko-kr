---
title: "메모리 덮어쓰기 확인 하려면 디버그 빌드를 사용 하 여 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f18a13992e41cd88bc8edec44f16b02da38ad10c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>디버그 빌드를 사용한 메모리 덮어쓰기 확인
메모리 덮어쓰기 확인 하려면 디버그 빌드를 사용 하려면 디버그에 대 한 프로젝트를 먼저 빌드해야 할 합니다. 그런 다음 응용 프로그램의 처음 부분을 이동 `InitInstance` 다음 줄을 추가 합니다.  
  
```  
afxMemDF |= checkAlwaysMemDF;  
```  
  
 디버그 메모리 할당자는 모든 메모리 할당 주위 보호 바이트를 배치 합니다. 하지만 바이트 이러한 보호, 이러한 변경 되었는지 여부 (덮어쓰기가 메모리)를 확인 하지 않으면 모든 소용이 없습니다. 그렇지 않으면 실제로 수 있는 버퍼 제공 되어 사용 메모리 덮어쓰기를 수 있습니다.  
  
 설정 하 여는 `checkAlwaysMemDF`를를 호출 하는 MFC 고쳐집니다는 `AfxCheckMemory` 에 대 한 호출 될 때마다 함수 **새** 또는 **삭제** 이루어집니다. 메모리 덮어쓰기 발견, 다음과 같은 추적 메시지를 생성 됩니다.  
  
```  
Damage Occurred! Block=0x5533  
```  
  
 이러한 메시지 중 하나를 참조 하는 경우 손상이 발생 한 위치를 확인 하는 코드를 단계별로 실행 되도록 해야 합니다. 메모리 덮어쓰기 발생 한 부분을 보다 정확 하 게 하려면에 대 한 명시적 호출을 만들 수 있습니다 `AfxCheckMemory` 직접 합니다. 예:  
  
```  
ASSERT(AfxCheckMemory());  
    DoABunchOfStuff();  
    ASSERT(AfxCheckMemory());  
```  
  
 첫 번째 ASSERT 성공 하는 경우 두 번째 식에 오류가 발생 하면 메모리 덮어쓰기 두 호출 간에 함수에서 발생 했을 의미 합니다.  
  
 응용 프로그램의 특성에 따라 있을 수도 있습니다. `afxMemDF` 하면 프로그램 실행이 너무 느리게도 테스트 합니다. `afxMemDF` 변수 하면 `AfxCheckMemory` 새로운를 호출할 때마다 호출 되 고 삭제를 합니다. 호출을 분산형 해야 하는 경우 `AfxCheckMemory`위에 표시 된 것 처럼 ()와 메모리 덮어쓰기를 그렇게 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [릴리스 빌드 문제 해결](../../build/reference/fixing-release-build-problems.md)