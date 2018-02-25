---
title: "sync_shared 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_shared
- stdext::sync_shared [C++], allocate
- stdext::sync_shared [C++], deallocate
- stdext::sync_shared [C++], equals
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aea3f774ecfff03e3c9738cf948f95d76773f063
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="syncshared-class"></a>sync_shared 클래스
뮤텍스를 사용하여 모든 할당자가 공유하는 캐시 개체에 대한 액세스를 제어하는 [동기화 필터](../standard-library/allocators-header.md)를 설명합니다.  
  
## <a name="syntax"></a>구문  
  
```
template <class Cache>  
class sync_shared
```  
  
#### <a name="parameters"></a>매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`Cache`|동기화 필터와 연결된 캐시 형식입니다. [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) 또는 [cache_suballoc](../standard-library/cache-suballoc-class.md)일 수 있습니다.|  
  
### <a name="member-functions"></a>멤버 함수  
  
|||  
|-|-|  
|[allocate](#allocate)|메모리 블록을 할당합니다.|  
|[deallocate](#deallocate)|지정된 위치부터 시작하여 저장소에서 지정된 개수의 개체를 해제합니다.|  
|[equals](#equals)|두 캐시가 같은지 비교합니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<allocators>  
  
 **네임스페이스:** stdext  
  
##  <a name="allocate"></a>  sync_shared::allocate  
 메모리 블록을 할당합니다.  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`count`|할당할 배열의 요소 수입니다.|  
  
### <a name="return-value"></a>반환 값  
 할당된 개체에 대한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 구성원 함수는 뮤텍스를 잠그고, `cache.allocate(count)`를 호출하고, 뮤텍스 잠금을 해제한 다음 이전 호출의 결과를 `cache.allocate(count)`에 반환합니다. `cache`는 현재 캐시 개체를 나타냅니다.  
  
##  <a name="deallocate"></a>  sync_shared::deallocate  
 지정된 위치부터 시작하여 저장소에서 지정된 개수의 개체를 해제합니다.  
  
```
void deallocate(void* ptr, std::size_t count);
```  
  
### <a name="parameters"></a>매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`ptr`|저장소에서 할당을 취소할 첫 번째 개체에 대한 포인터입니다.|  
|`count`|저장소에서 할당을 취소할 개체의 수입니다.|  
  
### <a name="remarks"></a>설명  
 이 구성원 함수는 뮤텍스를 잠그고, `cache.deallocate(ptr, count)`를 호출한 다음(여기서 `cache`는 캐시 개체를 나타냄) 뮤텍스 잠금을 해제합니다.  
  
##  <a name="equals"></a>  sync_shared::equals  
 두 캐시가 같은지 비교합니다.  
  
```
bool equals(const sync_shared<Cache>& Other) const;
```  
  
### <a name="parameters"></a>매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`Cache`|동기화 필터와 연결된 캐시 형식입니다.|  
|`Other`|같은지 비교할 캐시입니다.|  
  
### <a name="return-value"></a>반환 값  
 `cache.equals(Other.cache)`의 결과(여기서 `cache`는 캐시 개체를 나타냄)가 `true`이면 `true`이고 그렇지 않으면 `false`입니다.  
  
### <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [\<allocators>](../standard-library/allocators-header.md)



