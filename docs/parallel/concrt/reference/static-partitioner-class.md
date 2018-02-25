---
title: "static_partitioner 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
dev_langs:
- C++
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20dad961b694042c721f388c9a40e0bf99b9b77d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="staticpartitioner-class"></a>static_partitioner 클래스
`static_partitioner` 클래스는 `parallel_for`에서 반복하는 범위의 정적 분할을 나타냅니다. 파티셔너는 기본 스케줄러에서 사용할 수 있는 작업자 수만큼의 청크로 범위를 나눕니다.  
  
## <a name="syntax"></a>구문  
  
```
class static_partitioner;
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[static_partitioner](#ctor)|`static_partitioner` 개체를 생성합니다.|  
|[~ static_partitioner 소멸자](#dtor)|`static_partitioner` 개체를 제거합니다.|  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `static_partitioner`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** ppl.h  
  
 **네임스페이스:** 동시성  
  
##  <a name="dtor"></a> ~static_partitioner 

 `static_partitioner` 개체를 제거합니다.  
  
```
~static_partitioner();
```  
  
##  <a name="ctor"></a> static_partitioner 

 `static_partitioner` 개체를 생성합니다.  
  
```
static_partitioner();
```  
  
## <a name="see-also"></a>참고 항목  
 [concurrency 네임스페이스](concurrency-namespace.md)
