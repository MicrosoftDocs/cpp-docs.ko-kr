---
title: PROVIDER_COLUMN_ENTRY_STR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_STR
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_STR macro
ms.assetid: f1c27dd6-9ab8-4821-8685-d4dd15e76e88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ede31951c916c8b70b4942c3077442b5e2e3313
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="providercolumnentrystr"></a>PROVIDER_COLUMN_ENTRY_STR
공급자에서 지 원하는 특정 열을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
PROVIDER_COLUMN_ENTRY_STR(name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>매개 변수  
 *name*  
 [in] 열 이름입니다.  
  
 `ordinal`  
 [in] 열 번호입니다. 열이 책갈피 열, 하지 않는 한 열 번호는 0 아니어야 합니다.  
  
 `member`  
 [in] 데이터를 저장 하는 데이터 클래스의 멤버 변수입니다.  
  
## <a name="remarks"></a>설명  
 열 데이터 것으로 간주 되는 경우이 매크로 사용 하 여 [DBTYPE_STR](https://msdn.microsoft.com/en-us/library/ms711251.aspx)합니다.  
  
## <a name="example"></a>예제  
 참조 [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atldb.h  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 공급자 템플릿 매크로](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 공급자 템플릿 구조](../../data/oledb/ole-db-provider-template-architecture.md)   
 [OLE DB 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md)