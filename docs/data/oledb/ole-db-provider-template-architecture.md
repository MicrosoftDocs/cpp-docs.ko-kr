---
title: OLE DB 공급자 템플릿 구조
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
ms.openlocfilehash: 89e07f95853c3611b7cceaef3f247c220c630add
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509549"
---
# <a name="ole-db-provider-template-architecture"></a>OLE DB 공급자 템플릿 구조

## <a name="data-sources-and-sessions"></a>데이터 소스 및 세션

OLE DB 공급자 아키텍처는 데이터 원본 개체와 하나 이상의 세션을 포함 합니다. 데이터 원본 개체는 모든 공급자가 인스턴스화해야 하는 초기 개체입니다. 소비자 응용 프로그램은 데이터를 필요로 할 때 데이터 원본 개체를 공동 만들어 공급자를 시작 합니다. 데이터 원본 개체는 `IDBCreateSession` 소비자가 데이터 원본 개체에 연결 하는 데 사용 하는 세션 개체 (인터페이스 사용)를 만듭니다. ODBC 프로그래머는 데이터 원본 개체를와 동일한 것으로 간주할 수 있습니다 `HENV` `HDBC` .

![공급자 아키텍처](../../data/oledb/media/vc4twb1.gif "공급자 아키텍처")

**OLE DB 공급자 마법사**에서 만든 원본 파일과 함께 OLE DB 템플릿은 데이터 원본 개체를 구현 합니다. 세션은 OLE DB에 해당 하는 개체입니다 `TSession` .

## <a name="mandatory-and-optional-interfaces"></a>필수 및 선택적 인터페이스

OLE DB 공급자 템플릿은 필요한 모든 인터페이스에 대 한 미리 패키지 된 구현을 제공 합니다. 필수 및 선택적 인터페이스는 여러 유형의 개체에 대해 OLE DB에 의해 정의 됩니다.

- [데이터 원본](../../data/oledb/data-source-object-interfaces.md)

- [세션](../../data/oledb/session-object-interfaces.md)

- [행 집합](../../data/oledb/rowset-object-interfaces.md)

- [명령](../../data/oledb/command-object-interfaces.md)

- [트랜잭션](../../data/oledb/transaction-object-interfaces.md)

OLE DB 공급자 템플릿은 행 및 저장소 개체를 구현 하지 않습니다.

다음 표에서는 [OLE DB 2.6 SDK 설명서](/previous-versions/windows/desktop/ms722784(v=vs.85))에 따라 위에 나열 된 개체에 대 한 필수 및 선택적 인터페이스를 보여 줍니다.

|구성 요소|인터페이스|설명|
|---------------|---------------|-------------|
|[데이터 원본](../../data/oledb/data-source-object-interfaces.md) ([cdatasource](../../data/oledb/cdatasource-class.md))|강제로 `IDBCreateSession`<br /><br /> 강제로 `IDBInitialize`<br /><br /> 강제로 `IDBProperties`<br /><br /> 강제로 `IPersist`<br /><br /> 필드 `IConnectionPointContainer`<br /><br /> 필드 `IDBAsynchStatus`<br /><br /> 필드 `IDBDataSourceAdmin`<br /><br /> 필드 `IDBInfo`<br /><br /> 필드 `IPersistFile`<br /><br /> 필드 `ISupportErrorInfo`|소비자에서 공급자로의 연결입니다. 개체는 사용자 ID, 암호 및 데이터 원본 이름과 같은 연결에 대 한 속성을 지정 하는 데 사용 됩니다. 개체를 사용 하 여 데이터 원본 (만들기, 업데이트, 삭제, 테이블 등)을 관리할 수도 있습니다.|
|[세션](../../data/oledb/session-object-interfaces.md) ([csession](./cdataconnection-class.md#op_csession_amp))|강제로 `IGetDataSource`<br /><br /> 강제로 `IOpenRowset`<br /><br /> 강제로 `ISessionProperties`<br /><br /> 필드 `IAlterIndex`<br /><br /> 필드 `IAlterTable`<br /><br /> 필드 `IBindResource`<br /><br /> 필드 `ICreateRow`<br /><br /> 필드 `IDBCreateCommand`<br /><br /> 필드 `IDBSchemaRowset`<br /><br /> 필드 `IIndexDefinition`<br /><br /> 필드 `ISupportErrorInfo`<br /><br /> 필드 `ITableCreation`<br /><br /> 필드 `ITableDefinition`<br /><br /> 필드 `ITableDefinitionWithConstraints`<br /><br /> 필드 `ITransaction`<br /><br /> 필드 `ITransactionJoin`<br /><br /> 필드 `ITransactionLocal`<br /><br /> 필드 `ITransactionObject`|Session 개체는 소비자와 공급자 간의 단일 대화입니다. `HSTMT`여러 동시 세션이 활성화 될 수 있다는 점에서 ODBC와 비슷합니다.<br /><br /> 세션 개체는 OLE DB 기능을 얻기 위한 기본 링크입니다. 명령, 트랜잭션 또는 행 집합 개체를 가져오려면 session 개체를 통해 이동 합니다.|
|[행 집합](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|강제로 `IAccessor`<br /><br /> 강제로 `IColumnsInfo`<br /><br /> 강제로 `IConvertType`<br /><br /> 강제로 `IRowset`<br /><br /> 강제로 `IRowsetInfo`<br /><br /> 필드 `IChapteredRowset`<br /><br /> 필드 `IColumnsInfo2`<br /><br /> 필드 `IColumnsRowset`<br /><br /> 필드 `IConnectionPointContainer`<br /><br /> 필드 `IDBAsynchStatus`<br /><br /> 필드 `IGetRow`<br /><br /> 필드 `IRowsetChange`<br /><br /> 필드 `IRowsetChapterMember`<br /><br /> 필드 `IRowsetCurrentIndex`<br /><br /> 필드 `IRowsetFind`<br /><br /> 필드 `IRowsetIdentity`<br /><br /> 필드 `IRowsetIndex`<br /><br /> 필드 `IRowsetLocate`<br /><br /> 필드 `IRowsetRefresh`<br /><br /> 필드 `IRowsetScroll`<br /><br /> 필드 `IRowsetUpdate`<br /><br /> 필드 `IRowsetView`<br /><br /> 필드 `ISupportErrorInfo`<br /><br /> 필드 `IRowsetBookmark`|행 집합 개체는 데이터 원본의 데이터입니다. 개체는 해당 데이터의 바인딩과 데이터의 모든 기본 작업 (업데이트, 페치, 이동 및 기타)에 사용 됩니다. 데이터를 유지 하 고 조작 하기 위한 행 집합 개체가 항상 있습니다.|
|[명령](../../data/oledb/command-object-interfaces.md) ([CCommand](ccommand-class.md))|강제로 `IAccessor`<br /><br /> 강제로 `IColumnsInfo`<br /><br /> 강제로 `ICommand`<br /><br /> 강제로 `ICommandProperties`<br /><br /> 강제로 `ICommandText`<br /><br /> 강제로 `IConvertType`<br /><br /> 필드 `IColumnsRowset`<br /><br /> 필드 `ICommandPersist`<br /><br /> 필드 `ICommandPrepare`<br /><br /> 필드 `ICommandWithParameters`<br /><br /> 필드 `ISupportErrorInfo`<br /><br /> 필드 `ICommandStream`|Command 개체는 쿼리와 같은 데이터에 대 한 작업을 처리 합니다. 매개 변수가 있거나 매개 변수가 없는 문을 처리할 수 있습니다.<br /><br /> 또한 command 개체는 매개 변수 및 출력 열에 대 한 바인딩 처리를 담당 합니다. 바인딩은 행 집합의 열을 검색 하는 방법에 대 한 정보를 포함 하는 구조체입니다. 서 수, 데이터 형식, 길이 및 상태와 같은 정보를 포함 합니다.|
|[Transaction](../../data/oledb/transaction-object-interfaces.md) (선택 사항)|강제로 `IConnectionPointContainer`<br /><br /> 강제로 `ITransaction`<br /><br /> 필드 `ISupportErrorInfo`|트랜잭션 개체는 데이터 원본에 대 한 원자 단위 작업을 정의 하 고 이러한 작업 단위가 서로 어떻게 관련 되는지를 결정 합니다. 이 개체는 OLE DB 공급자 템플릿에서 직접 지원 되지 않습니다. 즉, 고유한 개체를 만듭니다.|

자세한 내용은 다음 항목을 참조하세요.

- [속성 맵](../../data/oledb/property-maps.md)

- [사용자 레코드](../../data/oledb/user-record.md)

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 인터페이스](/previous-versions/windows/desktop/ms709709(v=vs.85))<br/>
