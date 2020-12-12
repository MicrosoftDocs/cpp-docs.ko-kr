---
description: '자세한 정보: CCustomSession (CustomSess)'
title: CCustomSession(CustomSess.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidersession
- myprovidersess.h
- ccustomsession
- customsess.h
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
- CCustomSession class in CustomSess.H
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
ms.openlocfilehash: 0c090e01b5cef1bc0fccad8a1c23948fb9ea09b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170427"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession(CustomSess.H)

*사용자 지정* 세션에는 OLE DB 세션 개체에 대 한 선언 및 구현이 포함 되어 있습니다. 데이터 원본 개체는 세션 개체를 만들고 소비자와 공급자 간의 대화를 나타냅니다. 하나의 데이터 원본에 대해 여러 동시 세션을 열 수 있습니다. 의 상속 목록은 `CCustomSession` 다음과 같습니다.

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSession
class ATL_NO_VTABLE CCustomSession :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IGetDataSourceImpl<CCustomSession>,
   public IOpenRowsetImpl<CCustomSession>,
   public ISessionPropertiesImpl<CCustomSession>,
   public IObjectWithSiteSessionImpl<CCustomSession>,
   public IDBSchemaRowsetImpl<CCustomSession>,
   public IDBCreateCommandImpl<CCustomSession, CCustomCommand>
```

Session 개체는,, `IGetDataSource` 및에서 상속 `IOpenRowset` `ISessionProperties` `IDBCreateCommand` 됩니다. `IGetDataSource`인터페이스를 사용 하면 세션에서이를 만든 데이터 원본을 검색할 수 있습니다. 이는 사용자가 만든 데이터 원본 또는 데이터 원본이 제공할 수 있는 기타 정보에서 속성을 가져와야 하는 경우에 유용 합니다. `ISessionProperties`인터페이스는 세션에 대 한 모든 속성을 처리 합니다. `IOpenRowset`및 `IDBCreateCommand` 인터페이스는 데이터베이스 작업을 수행 하는 데 사용 됩니다. 공급자가 명령을 지 원하는 경우 인터페이스를 구현 `IDBCreateCommand` 합니다. 명령을 실행할 수 있는 명령 개체를 만드는 데 사용 됩니다. 공급자는 항상 개체를 구현 합니다 `IOpenRowset` . 공급자에서 행 집합을 생성 하는 데 사용 됩니다. 공급자의 기본 행 집합 (예: `"select * from mytable"` )입니다.

또한 마법사는 세 가지 세션 클래스인 `CCustomSessionColSchema` , 및을 생성 `CCustomSessionPTSchema` `CCustomSessionTRSchema` 합니다. 이러한 세션은 스키마 행 집합에 사용 됩니다. 공급자는 스키마 행 집합을 사용 하 여 소비자가 쿼리를 실행 하거나 데이터를 가져올 필요 없이 소비자에 게 메타 데이터를 반환할 수 있습니다. 메타 데이터 페치는 공급자의 기능을 찾는 것 보다 훨씬 빠를 수 있습니다.

OLE DB 사양을 사용 하려면 인터페이스를 구현 하는 공급자가 `IDBSchemaRowset` DBSCHEMA_COLUMNS, DBSCHEMA_PROVIDER_TYPES 및 DBSCHEMA_TABLES의 세 가지 스키마 행 집합 형식을 지원 해야 합니다. 마법사는 각 스키마 행 집합에 대 한 구현을 생성 합니다. 마법사에서 생성 되는 각 클래스에는 메서드가 포함 되어 있습니다 `Execute` . 이 `Execute` 메서드에서는 지원 되는 테이블, 열 및 데이터 형식에 대 한 데이터를 공급자에 게 반환할 수 있습니다. 이 데이터는 컴파일 타임에 알 수 있습니다.

## <a name="see-also"></a>참고 항목

[공급자 Wizard-Generated 파일](../../data/oledb/provider-wizard-generated-files.md)<br/>
