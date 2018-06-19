---
title: uninitialized_object 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
dev_langs:
- C++
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b9b10af535b0739d480326d616ee7587318bb5a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696177"
---
# <a name="uninitializedobject-class"></a>uninitialized_object 클래스
초기화 되지 않은 개체를 사용 하는 경우 throw 되는 예외입니다.  
  
## <a name="syntax"></a>구문  
  
```  
class uninitialized_object : public runtime_exception;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[uninitialized_object 생성자](#ctor)|`uninitialized_object` 클래스의 새 인스턴스를 초기화합니다.|  

  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `exception`  
  
 `runtime_exception`  
  
 `uninitialized_object`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** amprt.h  
  
 **네임스페이스:** 동시성  
## <a name="uninitialized_object__ctor"></a> unsupported_feature 

Unsupported_feature 예외의 새 인스턴스를 생성합니다.  
  
### <a name="syntax"></a>구문  
  
```  
explicit unsupported_feature(  
    const char * _Message ) throw();  
  
unsupported_feature() throw();  
```  
  
### <a name="parameters"></a>매개 변수  
 `_Message`  
 오류에 대한 설명입니다.  
  
### <a name="return-value"></a>반환 값  
 `unsupported_feature` 개체 

## <a name="see-also"></a>참고 항목  
 [Concurrency 네임스페이스(C++ AMP)](concurrency-namespace-cpp-amp.md)
