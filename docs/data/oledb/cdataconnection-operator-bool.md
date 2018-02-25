---
title: 'Cdataconnection:: Operator BOOL | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
dev_langs:
- C++
helpviewer_keywords:
- BOOL operator
- operator bool
ms.assetid: ad0bea7f-61ff-47f7-8127-32a31e3e9b9d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a29d4a3878750f2ca7e70eff032ac9d2cb6b986c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="cdataconnectionoperator-bool"></a>CDataConnection::operator BOOL
현재 세션이 열려 있는지 여부를 결정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
operator BOOL() throw();  
  
```  
  
## <a name="remarks"></a>설명  
 반환 **BOOL** (MFC typedef) 값입니다. **TRUE** 열려 있습니다; 현재 세션은 **FALSE** 현재 세션이 닫히면 것을 의미 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atldbcli.h  
  
## <a name="see-also"></a>참고 항목  
 [CDataConnection 클래스](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator bool](../../data/oledb/cdataconnection-operator-bool-ole-db.md)