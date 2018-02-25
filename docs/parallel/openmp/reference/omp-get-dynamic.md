---
title: omp_get_dynamic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 865104055fc98946c09152f328f4812af0120e64
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="ompgetdynamic"></a>omp_get_dynamic
런타임에서 후속 병렬 영역에서 사용할 수 있는 스레드 수를 조정할 수 하는 경우를 나타내는 값을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
int omp_get_dynamic();  
```  
  
## <a name="return-value"></a>반환 값  
 0이 아니면 동적 조정 스레드는 사용할 수 있습니다.  
  
## <a name="remarks"></a>설명  
 스레드 동적인 조절을 지정 된 [omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) 및 [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)합니다.  
  
 자세한 내용은 참조 [3.1.7 omp_set_dynamic 함수](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)합니다.  
  
## <a name="example"></a>예  
 참조 [omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) 사용 하는 예제에 대 한 `omp_get_dynamic`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [함수](../../../parallel/openmp/reference/openmp-functions.md)