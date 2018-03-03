---
title: "2.6.1 master 구문 | Microsoft Docs"
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
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2517e19b49f1314e7432bb265756193ea3bb8f91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="261-master-construct"></a>2.6.1 master 구문
**마스터** 지시문 팀의 마스터 스레드에 의해 실행 되는 구조화 된 블록을 지정 하는 구조를 식별 합니다. 구문은 **마스터** 지시문은 다음과 같습니다.  
  
```  
#pragma omp master new-linestructured-block  
```  
  
 팀의 다른 스레드를 연결된 하는 구조화 된 블록을 실행 하지 마십시오. 항목을 또는 종료를 master 구문 중 하나에 없는 묵시적된 장벽이 있습니다.