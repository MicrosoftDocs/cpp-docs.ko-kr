---
title: CBookmark 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c14fde6fb07a35ef9e2955ce61f991bede6b11a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094753"
---
# <a name="cbookmark-class"></a>CBookmark 클래스
버퍼에서 책갈피 값을 보유합니다.  
  
## <a name="syntax"></a>구문

```cpp
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase
  
template <>  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
#### <a name="parameters"></a>매개 변수  
 `nSize`  
 책갈피 버퍼의 바이트의 크기입니다. 때 `nSize` 가 0 인 책갈피 버퍼 런타임 시 동적으로 생성 됩니다.  
  
## <a name="members"></a>멤버  
  
### <a name="methods"></a>메서드  
  
|||  
|-|-|  
|[CBookmark](../../data/oledb/cbookmark-class.md)|생성자|  
|[GetBuffer](../../data/oledb/cbookmark-getbuffer.md)|버퍼에 대 한 포인터를 검색합니다.|  
|[GetSize](../../data/oledb/cbookmark-getsize.md)|버퍼의 바이트의 크기를 검색 합니다.|  
|[SetBookmark](../../data/oledb/cbookmark-setbookmark.md)|책갈피 값을 설정합니다.|  
  
### <a name="operators"></a>연산자  
  
|||  
|-|-|  
|[operator =](../../data/oledb/cbookmark-operator-equal.md)|값을 할당 `CBookmark` 다른 클래스입니다.|  
  
## <a name="remarks"></a>설명  
 **CBookmark\<0 >** 의 템플릿 특수화 `CBookmark`; 버퍼 런타임 시 동적으로 생성 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atldbcli.h  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)