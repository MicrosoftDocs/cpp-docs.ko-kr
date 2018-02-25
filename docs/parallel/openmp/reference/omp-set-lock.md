---
title: omp_set_lock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_set_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_set_lock OpenMP function
ms.assetid: ded839cb-ca19-403f-8622-eb52ce512d31
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 40d56dd19764ac1c252e7c483d7ef6758e2bcb04
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="ompsetlock"></a>omp_set_lock
블록은 잠금의 있을 때까지 실행을 스레드입니다.  
  
## <a name="syntax"></a>구문  
  
```  
void omp_set_lock(  
   omp_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>설명  
 다음은 각 문자에 대한 설명입니다.  
  
 `lock`  
 형식의 변수 [omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) 를 사용 하 여 초기화 된 [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)합니다.  
  
## <a name="remarks"></a>설명  
 자세한 내용은 참조 [3.2.3 omp_set_lock and omp_set_nest_lock 함수](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)합니다.  
  
## <a name="examples"></a>예제  
 참조 [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) 사용 하는 예제에 대 한 `omp_set_lock`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [함수](../../../parallel/openmp/reference/openmp-functions.md)