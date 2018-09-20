---
title: omp_set_num_threads | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_num_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae9dbe52dba47208844b73175f20edcc591a3ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444946"
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads

재정의 되지 않으면 후속 병렬 지역의 스레드 수가 설정 된 [num_threads](../../../parallel/openmp/reference/num-threads.md) 절.

## <a name="syntax"></a>구문

```
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>매개 변수

*num_threads*<br/>
병렬 영역에 있는 스레드의 수입니다.

## <a name="remarks"></a>설명

자세한 내용은 [3.1.1 omp_set_num_threads 함수](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)합니다.

## <a name="example"></a>예제

참조 [omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md) 사용 하는 예제에 대 한 `omp_set_num_threads`합니다.

## <a name="see-also"></a>참고 항목

[함수](../../../parallel/openmp/reference/openmp-functions.md)