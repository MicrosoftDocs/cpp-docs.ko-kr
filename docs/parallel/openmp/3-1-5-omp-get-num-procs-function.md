---
title: "3.1.5 omp_get_num_procs 함수 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: bbfbf17b-0c68-4ba6-a25d-07c36ecb551f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 22ae70cd2a98feb610d0a1a3d9d4e073e0875e48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="315-ompgetnumprocs-function"></a>3.1.5 omp_get_num_procs 함수
`omp_get_num_procs` 함수는 함수가 호출 되는 시간에 프로그램에 사용할 수 있는 프로세서 수를 반환 합니다. 형식은 다음과 같습니다.  
  
```  
#include <omp.h>  
int omp_get_num_procs(void);  
```