---
title: "CDefaultHashTraits 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
dev_langs:
- C++
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2407ffdd5d8ea327cd4669f2c33ccda5e0246d6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits 클래스
이 클래스는 해시 값을 계산 하기 위한 정적 함수를 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```
template<typename T>  
class CDefaultHashTraits
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 컬렉션에 저장할 데이터의 형식입니다.  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CDefaultHashTraits::Hash](#hash)|(정적) 지정된 된 요소에 대 한 해시 값을 계산 하려면이 함수를 호출 합니다.|  
  
## <a name="remarks"></a>설명  
 이 클래스는 지정된 된 요소에 대 한 해시 값을 반환 하는 단일 정적 함수를 포함 합니다. 이 클래스에서 사용 된는 [CDefaultElementTraits 클래스](../../atl/reference/cdefaultelementtraits-class.md)합니다.  
  
 자세한 내용은 참조 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlcoll.h  
  
##  <a name="hash"></a>CDefaultHashTraits::Hash  
 지정된 된 요소에 대 한 해시 값을 계산 하려면이 함수를 호출 합니다.  
  
```
static ULONG Hash(const T& element) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `element`  
 요소입니다.  
  
### <a name="return-value"></a>반환 값  
 해시 값을 반환합니다.  
  
### <a name="remarks"></a>설명  
 기본 해싱 알고리즘은 매우 간단: 반환 값은 요소 수입니다. 더 복잡 한 알고리즘을 해야 하는 경우이 함수를 재정의 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [클래스 개요](../../atl/atl-class-overview.md)
