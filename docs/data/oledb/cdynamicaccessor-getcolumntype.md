---
title: 'Cdynamicaccessor:: Getcolumntype | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
dev_langs:
- C++
helpviewer_keywords:
- GetColumnType method
ms.assetid: ac96a2e9-6049-4eb5-9718-9f5f5446b74e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4e2b0ad31c96afd63424d07767f25327eabce3e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorgetcolumntype"></a>CDynamicAccessor::GetColumnType
지정 된 열의 데이터 형식을 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```
bool GetColumnType(DBORDINAL nColumn,   
  DBTYPE* pType) const throw();  
```  
  
#### <a name="parameters"></a>매개 변수  
 `nColumn`  
 [in] 열 번호입니다. 열 번호는 1부터 시작 합니다. 0 값이 있는 경우 책갈피 열을 참조 합니다.  
  
 `pType`  
 [out] 지정 된 열의 데이터 형식에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 반환 **true** 성공 또는 **false** 실패 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atldbcli.h  
  
## <a name="see-also"></a>참고 항목  
 [CDynamicAccessor 클래스](../../data/oledb/cdynamicaccessor-class.md)   
 [DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx)