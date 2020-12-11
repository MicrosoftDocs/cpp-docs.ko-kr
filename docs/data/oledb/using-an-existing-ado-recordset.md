---
description: '자세한 정보: 기존 ADO 레코드 집합 사용'
title: 기존 ADO 레코드 집합 사용
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 4b5c3b5f621f3cbdba6f2d42fd95436495a5661e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160950"
---
# <a name="using-an-existing-ado-recordset"></a>기존 ADO 레코드 집합 사용

OLE DB 소비자 템플릿과 ADO (Active Data Objects)를 혼합 하려면 ADO를 사용 하 여 레코드 집합을 엽니다 (OLE DB 소비자 템플릿의 행 집합에 해당). 레코드 집합이 있는 경우 다음을 수행 하 여 OLE DB 행 집합에 연결 합니다.

1. `QueryInterface`및 포인터에 대해를 호출 `IRowset` `IAccessor` 합니다.

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk* 는 `IUnknown` ADO 레코드 집합의 개체를 가리킵니다.

1. 접근자와 행 집합을 적절 한 OLE DB 소비자 템플릿 클래스에 연결 합니다.

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)
