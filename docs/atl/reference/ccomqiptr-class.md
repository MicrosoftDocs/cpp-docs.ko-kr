---
title: "CComQIPtr 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b63e584b7c4620be0e77da034a2a419b80cf741
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="ccomqiptr-class"></a>CComQIPtr 클래스
COM 인터페이스 포인터를 관리 하기 위한 스마트 포인터 클래스입니다.  
  
## <a name="syntax"></a>구문  
  
```
template<class T, const IID* piid= &__uuidof(T)>  
class CComQIPtr: public CComPtr<T>
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 저장할 수에 대 한 포인터의 유형을 지정 하는 COM 인터페이스입니다.  
  
 `piid`  
 IID에 대 한 포인터 `T`합니다.  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CComQIPtr::CComQIPtr](#ccomqiptr)|생성자입니다.|  
  
### <a name="public-operators"></a>Public 연산자  
  
|이름|설명|  
|----------|-----------------|  
|[CComQIPtr::operator =](#operator_eq)|멤버 포인터에 대 한 포인터를 할당합니다.|  
  
## <a name="remarks"></a>설명  
 ATL 사용 하 여 `CComQIPtr` 및 [CComPtr](../../atl/reference/ccomptr-class.md) 에서 파생 되는 COM 인터페이스 포인터를 관리 하려면 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)합니다. 자동 참조에 대 한 호출을 통해 계산을 수행 하는 두 클래스 모두 `AddRef` 및 **릴리스**합니다. 오버 로드 된 연산자는 포인터 작업을 처리 합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 [CComPtr](../../atl/reference/ccomptr-class.md)  
  
 `CComQIPtr`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlcomcli.h  
  
##  <a name="ccomqiptr"></a>CComQIPtr::CComQIPtr  
 생성자입니다.  
  
```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `lp`  
 인터페이스 포인터를 초기화 하는 데 사용 합니다.  
  
 `T`  
 COM 인터페이스입니다.  
  
 `piid`  
 IID에 대 한 포인터 `T`합니다.  
  
##  <a name="operator_eq"></a>CComQIPtr::operator =  
 대입 연산자입니다.  
  
```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `lp`  
 인터페이스 포인터를 초기화 하는 데 사용 합니다.  
  
 `T`  
 COM 인터페이스입니다.  
  
 `piid`  
 IID에 대 한 포인터 `T`합니다.  
  
### <a name="return-value"></a>반환 값  
 업데이트 된에 대 한 포인터를 반환 `CComQIPtr` 개체입니다.  
  
## <a name="see-also"></a>참고 항목  
 [CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)   
 [CComQIPtr::CComQIPtr](#ccomqiptr)   
 [CComPtrBase 클래스](../../atl/reference/ccomptrbase-class.md)   
 [클래스 개요](../../atl/atl-class-overview.md)   
 [CComQIPtrElementTraits 클래스](../../atl/reference/ccomqiptrelementtraits-class.md)
