---
description: '자세한 정보: 데이터 원본 개체 인터페이스'
title: 데이터 소스 개체 인터페이스
ms.date: 10/24/2018
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
ms.openlocfilehash: ecc37ca4286e288939ccd15bdcd073379c27f7c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287621"
---
# <a name="data-source-object-interfaces"></a>데이터 소스 개체 인터페이스

다음 표에서는 데이터 원본 개체에 대해 OLE DB에 의해 정의 된 필수 및 선택적 인터페이스를 보여 줍니다.

|인터페이스|필수 여부|OLE DB 템플릿에서 구현 됩니까?|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|필수|예|
|`IDBInitialize`|필수|예|
|`IDBProperties`|필수|예|
|[IPersist](/windows/win32/api/objidl/nn-objidl-ipersist)|필수|예|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|선택 사항|아니요|
|`IDBDataSourceAdmin`|선택 사항|아니요|
|`IDBInfo`|선택 사항|아니요|
|[IPersistFile](/windows/win32/api/objidl/nn-objidl-ipersistfile)|선택 사항|아니요|
|`ISupportErrorInfo`|선택 사항|아니요|

데이터 소스 개체는 `IDBProperties` `IDBInitialize` 상속을 통해, 및 인터페이스를 구현 합니다 `IDBCreateSession` . 이러한 구현 클래스 중 하나에서 상속 하거나 상속 하지 않고 추가 기능을 지원 하도록 선택할 수 있습니다. 인터페이스를 지원 하려면 `IDBDataSourceAdmin` 클래스에서 상속 해야 합니다 `IDBDataSourceAdminImpl` .

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
