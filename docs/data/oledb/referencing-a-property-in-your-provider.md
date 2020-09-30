---
title: 공급자의 속성 참조
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: ecb11c54d4c5926fbead0196c441ec23e8b0891f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509517"
---
# <a name="referencing-a-property-in-your-provider"></a>공급자의 속성 참조

원하는 속성에 대 한 속성 그룹 및 속성 ID를 찾습니다. 자세한 내용은 **OLE DB 프로그래머 참조**의 [OLE DB 속성](/previous-versions/windows/desktop/ms722734(v=vs.85)) 을 참조 하세요.

다음 예에서는 행 집합에서 속성을 가져오려고 한다고 가정 합니다. Session 또는 command를 사용 하는 코드는 유사 하지만 다른 인터페이스를 사용 합니다.

속성 그룹을 생성자에 대 한 매개 변수로 사용 하 여 [CDBPropSet](../../data/oledb/cdbpropset-class.md) 개체를 만듭니다. 다음은 그 예입니다.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

속성에 할당할 속성 ID 및 값을 전달 하 여 [AddProperty](./cdbpropset-class.md#addproperty)를 호출 합니다. 값의 형식은 사용 중인 속성에 따라 달라 집니다.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

인터페이스를 사용 `IRowset` 하 여를 호출 `GetProperties` 합니다. 속성 집합을 매개 변수로 전달 합니다. 최종 코드는 다음과 같습니다.

```cpp
CAgentRowset<CCustomCommand>* pRowset = (CAgentRowset<CCustomCommand>*) pThis;

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

[OLE DB 공급자 템플릿 사용](../../data/oledb/working-with-ole-db-provider-templates.md)
