---
description: 자세한 내용은 OLE DB 소비자 템플릿 참조를 참조 하세요.
title: OLE DB 소비자 템플릿 참조
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
ms.openlocfilehash: e904237a7fbdef84c5f7f902ba352301a608b544
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286958"
---
# <a name="ole-db-consumer-templates-reference"></a>OLE DB 소비자 템플릿 참조

OLE DB Consumer 템플릿에는 다음과 같은 클래스가 포함 되어 있습니다. 참조 자료에는 [OLE DB 소비자 템플릿에 대 한 매크로](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)항목도 포함 되어 있습니다.

## <a name="session-classes"></a>세션 클래스

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
데이터 원본에 대 한 연결을 관리 합니다. 이 클래스는 필요한 개체 (데이터 소스 및 세션)와 데이터 소스에 연결할 때 수행 해야 하는 작업의 일부를 캡슐화 하기 때문에 클라이언트를 만드는 데 유용 합니다.

[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
데이터 원본에 대 한 공급자를 통해 연결을 나타내는 OLE DB 데이터 소스 개체에 해당 합니다. 단일 연결에 대해 각각 개체로 표시 되는 하나 이상의 데이터베이스 세션을 `CSession` 수행할 수 있습니다.

[CEnumerator](../../data/oledb/cenumerator-class.md)<br/>
사용 가능한 데이터 소스에 대 한 행 집합 정보를 검색 하는 OLE DB 열거자 개체에 해당 합니다.

[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
에서 `CEnumerator` 열거자 행 집합의 데이터에 액세스 하는 데 사용 됩니다. 이 행 집합은 현재 열거자에서 표시 되는 데이터 소스와 열거자로 구성 됩니다.

[CSession](../../data/oledb/csession-class.md)<br/>
단일 데이터베이스 액세스 세션을 나타냅니다. 하나 이상의 세션을 각 개체와 연결할 수 있습니다 `CDataSource` .

## <a name="accessor-classes"></a>접근자 클래스

[CAccessor](../../data/oledb/caccessor-class.md)<br/>
정적으로 데이터 소스에 바인딩된 레코드에 사용 됩니다. 데이터 소스의 구조를 알고 있는 경우이 접근자 클래스를 사용 합니다.

[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
모든 접근자 클래스의 기본 클래스입니다.

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
행 집합의 열 정보를 기반으로 런타임에 만들 수 있는 접근자입니다. 데이터 원본의 구조를 모르는 경우이 클래스를 사용 하 여 데이터를 검색 합니다.

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
명령 형식을 알 수 없는 경우 사용할 수 있는 접근자입니다. `ICommandWithParameters`공급자가 인터페이스를 지 원하는 경우 인터페이스를 호출 하 여 매개 변수 정보를 가져옵니다.

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
데이터베이스의 기본 구조에 대해 알지 못하는 경우 데이터 원본에 액세스할 수 있습니다.

[CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
와 유사 `CDynamicStringAccessor` 합니다. 단,이 클래스는 데이터 저장소에서 액세스할 수 있는 데이터를 ANSI 문자열 데이터로 요청 합니다.

[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
와 유사 합니다 `CDynamicStringAccessor` . 단,이 클래스는 데이터 저장소에서 데이터를 유니코드 문자열 데이터로 액세스 하도록 요청 합니다.

[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
열 및 명령 매개 변수를 모두 처리 하는 메서드가 포함 된 접근자입니다. 이 클래스를 사용 하면 공급자가 형식을 변환할 수 있는 한 모든 데이터 형식을 사용할 수 있습니다.

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
클래스에서 매개 변수 또는 출력 열을 지원 하지 않도록 하려면를 템플릿 인수로 사용할 수 있습니다.

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)<br/>
와 유사 `CDynamicStringAccessor` 합니다. 단,이 클래스는 데이터 저장소에서 액세스 한 모든 데이터를 XML 형식 (태그가 지정 된) 데이터로 변환 합니다.

## <a name="rowset-classes"></a>행 집합 클래스

[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)<br/>
행 집합 및 관련 접근자를 캡슐화 합니다.

[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
배열 구문을 사용 하 여 행 집합의 요소에 액세스 하는 데 사용 됩니다.

[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
단일 호출로 여러 행 핸들을 검색 하 여 행을 대량으로 인출 및 조작 하는 데 사용 됩니다.

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
는 명령이 행 집합을 반환 하지 않는 경우 템플릿 인수로 사용할 수 있습니다.

[CRestrictions](../../data/oledb/crestrictions-class.md)<br/>
스키마 행 집합에 대 한 제한을 지정 하는 데 사용 됩니다.

[CRowset](../../data/oledb/crowset-class.md)<br/>
행 집합 데이터를 조작, 설정 및 검색 하는 데 사용 됩니다.

[CStreamRowset](../../data/oledb/cstreamrowset-class.md)<br/>
`ISequentialStream`행 집합이 아닌 개체를 반환한 다음 메서드를 사용 하 여 `Read` XML 형식으로 데이터를 검색 합니다. SQL Server 2000는 서식 지정을 수행 합니다 .이 기능은 SQL Server 2000 에서만 작동 합니다.

[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
, `IRowsetNotify` 및 메서드에 대 한 빈 함수를 사용 하 여에 대 한 더미 구현을 제공 `IRowsetNotify` `OnFieldChange` `OnRowChange` `OnRowsetChange` 합니다.

[스키마 행 집합 클래스 및 Typedef 클래스](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)

OLE DB 템플릿은 OLE DB 스키마 행 집합에 해당 하는 클래스 집합을 제공 합니다.

## <a name="command-classes"></a>명령 클래스

[CCommand](../../data/oledb/ccommand-class.md)<br/>
매개 변수 기반 OLE DB 명령을 설정 하 고 실행 하는 데 사용 됩니다. 단순히 단순 행 집합을 열려면를 `CTable` 대신 사용 합니다.

[CMultipleResults](../../data/oledb/cmultipleresults-class.md)<br/>
`CCommand`명령을 사용 하 여 여러 결과 집합을 처리 하려고 할 때 템플릿의 템플릿 인수로 사용 됩니다.

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
`CCommand`접근자 클래스 인수를 사용 하는 및 등의 템플릿 클래스에 대 한 템플릿 인수로 사용 `CTable` 됩니다. `CNoAccessor`클래스가 매개 변수 또는 출력 열을 지원 하지 않도록 하려면를 사용 합니다.

[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)<br/>
`CCommand`명령을 사용 하 여 단일 행 집합을 처리 하려고 할 때 템플릿의 템플릿 인수로 사용 됩니다. `CNoMultipleResults` 템플릿 인수에 대 한 기본값입니다.

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
`CCommand` `CTable` 명령 또는 테이블이 행 집합을 반환 하지 않는 경우 또는의 템플릿 인수로 사용 됩니다.

[CTable](../../data/oledb/ctable-class.md)<br/>
매개 변수 없이 간단한 행 집합에 액세스 하는 데 사용 됩니다.

## <a name="property-classes"></a>속성 클래스

[CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
소비자가 속성 정보를 필요로 하는 속성 Id의 배열을 전달 하는 데 사용 됩니다. 속성은 하나의 속성 집합에 속합니다.

[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
공급자의 속성을 설정 하는 데 사용 됩니다.

## <a name="bookmark-class"></a>Bookmark 클래스

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
행 집합의 데이터에 액세스 하기 위한 인덱스로 사용 됩니다.

## <a name="error-class"></a>Error 클래스

[CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)<br/>
OLE DB 오류 정보를 검색 하는 데 사용 됩니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 참조](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 템플릿](../../data/oledb/ole-db-templates.md)
