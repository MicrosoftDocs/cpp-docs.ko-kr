---
title: "3.3.2 omp_get_wtick 함수 | Microsoft Docs"
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
ms.assetid: 1ad08500-bcb0-40d9-a81f-f131819006c9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 926ed8551ce032a52232a023a3f191a1b7efb233
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="332-ompgetwtick-function"></a>3.3.2 omp_get_wtick 함수
`omp_get_wtick` 함수 반환 배정밀도 부동 소수점 값 (초)의 수와 같지 연속 클록 틱 간 합니다. 형식은 다음과 같습니다.  
  
```  
#include <omp.h>  
double omp_get_wtick(void);  
```