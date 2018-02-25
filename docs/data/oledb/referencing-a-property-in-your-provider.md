---
title: "공급자의 속성 참조 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3a034c1f925a5b5d422be234118782b283a3d74c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="referencing-a-property-in-your-provider"></a>공급자의 속성 참조
원하는 속성에 대 한 속성 그룹과 속성 ID를 찾습니다. 자세한 내용은 참조 [OLE DB 속성](https://msdn.microsoft.com/en-us/library/ms722734.aspx) 에 *OLE DB Programmer's Reference*합니다.  
  
 다음 예에서는 행 집합에서 속성 가져오기 하려는 가정 합니다. 세션 또는 명령에 대 한 코드는 유사 하지만 서로 다른 인터페이스를 사용 합니다.  
  
 만들기는 [CDBPropSet](../../data/oledb/cdbpropset-class.md) 개체 생성자에 매개 변수로 속성 그룹을 사용 하 여 합니다. 예:  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
```  
  
 호출 [AddProperty](../../data/oledb/cdbpropset-addproperty.md), 속성에 할당할 속성 ID와 값을 전달 합니다. 값의 형식을 사용 하는 속성에 따라 달라 집니다.  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_IRowsetChange, true);  

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);  
```  
  
 사용 하 여는 `IRowset` 호출할 인터페이스 **GetProperties**합니다. 매개 변수로 설정할 속성을 전달 합니다. 최종 코드는 다음과 같습니다.  
  
```  
CAgentRowset<CMyProviderCommand>* pRowset = (CAgentRowset<CMyProviderCommand>*) pThis;  
  
CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;  
  
DBPROPIDSET set;  
set.AddPropertyID(DBPROP_BOOKMARKS);  

DBPROPSET* pPropSet = NULL;  
ULONG ulPropSet = 0;  

HRESULT hr;  
  
if (spRowsetProps)  
   hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);  
  

if (pPropSet)  
{  
   CComVariant var = pPropSet->rgProperties[0].vValue;  
   CoTaskMemFree(pPropSet->rgProperties);  
   CoTaskMemFree(pPropSet);  
  
   if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))  
   {  
      ...  // Use property here  
   }  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 공급자 템플릿을 사용하여 작업](../../data/oledb/working-with-ole-db-provider-templates.md)