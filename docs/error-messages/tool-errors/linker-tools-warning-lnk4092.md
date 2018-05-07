---
title: 링커 도구 경고 LNK4092 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4092
dev_langs:
- C++
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72edd9e75dbc781355396e38f767a64c1ded3aa9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4092"></a>링커 도구 경고 LNK4092
쓰기 가능한 공유 섹션 'section'에 재배치가 있습니다. 이미지가 올바르게 실행 되지 않을 수 있습니다.  
  
 링커는 잠재적으로 심각한 문제를 경고 하는 공유 섹션에 있는 경우이 경고를 내보냅니다.  
  
 여러 프로세스 간에 데이터를 공유 하는 한 가지 방법은 섹션 "공유 합니다."로 표시 됩니다. 그러나 섹션을 공유로 표시 문제가 발생할 수 있습니다. 예를 들어 공유 데이터 섹션에이 선언을 포함 하는 DLL이 있는:  
  
```  
int var = 1;  
int *pvar = &var;  
```  
  
 링커 확인할 수 없는 `pvar` DLL을 메모리에 로드에 해당 값에 따라 달라, 따라서 가져가서 지므로 DLL의 합니다. DLL의 주소 메모리에 로드할 때 `var` 해결할 수 있습니다 및 `pvar` 할당 합니다. 다른 프로세스가 동일한 DLL이 로드 동시에 로드할 수 없는 경우 주소의 주소를 위한 재배치 `var` 두 번째 프로세스와 첫 번째 프로세스의 주소 공간 잘못 된 주소를 가리키게 됩니다에 대 한 업데이트 됩니다.