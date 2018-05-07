---
title: IDBCreateSessionImpl 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateSessionImpl class
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3e027faa11ec7c2a2b6c8d29ef99fe95419a7594
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl 클래스
에 대 한 구현을 제공는 [IDBCreateSession](https://msdn.microsoft.com/en-us/library/ms724076.aspx) 인터페이스입니다.  
  
## <a name="syntax"></a>구문

```cpp
template <class T, class SessionClass>  
class ATL_NO_VTABLE IDBCreateSessionImpl   
   : public IDBCreateSession  
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 파생 클래스  
  
 `SessionClass`  
 세션 개체입니다.  
  
## <a name="members"></a>멤버  
  
### <a name="interface-methods"></a>인터페이스 메서드  
  
|||  
|-|-|  
|[CreateSession](../../data/oledb/idbcreatesessionimpl-createsession.md)|데이터 원본 개체에서 새 세션을 만들고 새로 만들어진된 세션의 요청 된 인터페이스를 반환 합니다.|  
  
## <a name="remarks"></a>설명  
 데이터 원본 개체에 필수 인터페이스입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atldb.h  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 공급자 템플릿 구조](../../data/oledb/ole-db-provider-template-architecture.md)