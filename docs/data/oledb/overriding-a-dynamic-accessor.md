---
description: '자세한 정보: 동적 접근자 재정의'
title: 동적 접근자 재정의
ms.date: 10/19/2018
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
- overriding, dynamic accessors
ms.assetid: cbefd156-6da5-490d-b795-c2d7d874f7ce
ms.openlocfilehash: 1057b59d7b2cd6b6f5e83511d9dd10e3726f648d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286763"
---
# <a name="overriding-a-dynamic-accessor"></a>동적 접근자 재정의

와 같은 동적 접근자를 사용 하는 경우 `CDynamicAccessor` 명령 `Open` 메서드는 열린 행 집합의 열 정보에 따라 자동으로 접근자를 만듭니다. 동적 접근자를 재정의 하 여 열이 바인딩되는 방식을 정확 하 게 제어할 수 있습니다.

동적 접근자를 재정의 하려면 **`false`** 메서드에 마지막 매개 변수로를 전달 합니다 `CCommand::Open` . 이렇게 하면 `Open` 접근자가 자동으로 생성 되지 않습니다. 그런 다음 `GetColumnInfo` `AddBindEntry` 바인딩할 각 열에 대해를 호출 하 고을 호출할 수 있습니다. 다음 코드에서는이 작업을 수행 하는 방법을 보여 줍니다.

```cpp
USES_CONVERSION;
double   dblProductID;

CCommand<CDynamicAccessor> product;
// Open the table, passing false to prevent automatic binding
product.Open(session, _T("Select * FROM Products"), NULL, NULL, DBGUID_DEFAULT, false);


ULONG         nColumns;
DBCOLUMNINFO*   pColumnInfo;
// Get the column information from the opened rowset.
product.GetColumnInfo(&nColumns, &pColumnInfo);

// Bind the product ID as a double.
pColumnInfo[0].wType          = DBTYPE_R8;
pColumnInfo[0].ulColumnSize = 8;
product.AddBindEntry(pColumnInfo[0]);

// Bind the product name as it is.
product.AddBindEntry(pColumnInfo[1]);

// Bind the reorder level as a string.
pColumnInfo[8].wType          = DBTYPE_STR;
pColumnInfo[8].ulColumnSize = 10;
product.AddBindEntry(pColumnInfo[8]);

// You have finished specifying the bindings. Go ahead and bind.
product.Bind();
// Free the memory for the column information that was retrieved in
// previous call to GetColumnInfo.
CoTaskMemFree(pColumnInfo);


char*   pszProductName;
char*   pszReorderLevel;
bool   bRC;

// Loop through the records tracing out the information.
while (product.MoveNext() == S_OK)
{
   bRC = product.GetValue(1, &dblProductID);
   pszProductName   = (char*)product.GetValue(2);
   pszReorderLevel  = (char*)product.GetValue(9);

   ATLTRACE(_T("Override = %lf \"%s\" \"%s\"\n"), dblProductID,
      A2T(pszProductName), A2T(pszReorderLevel));
}
```

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)
