---
title: 'Cdbpropidset:: Cdbpropidset | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class, constructor
ms.assetid: e68cc20e-fce2-4cc1-9e9d-05c542334cc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eb1aa5b832e8be0e90e34c32c9ad76a8c1c314f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090701"
---
# <a name="cdbpropidsetcdbpropidset"></a>CDBPropIDSet::CDBPropIDSet
생성자입니다. 초기화는 **rgProperties**, **cProperties**, 및 (옵션) **guidPropertySet** 의 필드는 [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) 구조입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
      CDBPropIDSet(const GUID& guid);  

CDBPropIDSet(const CDBPropIDSet& propidset);  

CDBPropIDSet();  
```  
  
#### <a name="parameters"></a>매개 변수  
 `guid`  
 [in] GUID를 초기화 하는 데 사용 된 **guidPropertySet** 필드입니다.  
  
 *propidset*  
 [in] 복사 생성을 위한 다른 `CDBPropIDSet` 개체입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atldbcli.h  
  
## <a name="see-also"></a>참고 항목  
 [CDBPropIDSet 클래스](../../data/oledb/cdbpropidset-class.md)   
 [CDBPropIDSet::SetGUID](../../data/oledb/cdbpropidset-setguid.md)