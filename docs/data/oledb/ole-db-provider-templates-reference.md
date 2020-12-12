---
description: 자세한 내용은 OLE DB 공급자 템플릿 참조를 참조 하세요.
title: OLE DB 공급자 템플릿 참조
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
ms.openlocfilehash: 021241bff80a72f665fb0c67f9f0877ec022992b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317001"
---
# <a name="ole-db-provider-templates-reference"></a>OLE DB 공급자 템플릿 참조

OLE DB 공급자 템플릿에 대 한 클래스와 인터페이스는 다음과 같은 범주로 그룹화 할 수 있습니다. 참조 자료에는 [OLE DB 공급자 템플릿의 매크로](../../data/oledb/macros-for-ole-db-provider-templates.md)에 대 한 정보도 포함 되어 있습니다.

클래스는 다음 명명 규칙을 사용 합니다. 패턴으로 이름이 지정 된 클래스는 `IWidgetImpl` 인터페이스의 구현을 제공 `IWidget` 합니다.

## <a name="session-classes"></a>세션 클래스

[IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
데이터 원본 개체에서 새 세션을 만들고 새로 만든 세션에서 요청 된 인터페이스를 반환 합니다. 데이터 원본 개체에 대 한 필수 인터페이스입니다.

[ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
속성 집합 맵에 의해 정의 된 정적 함수를 호출 하 여 세션 속성을 구현 합니다. 속성 집합 맵은 session 클래스에서 지정 해야 합니다. 세션에 대 한 필수 인터페이스입니다.

## <a name="rowset-classes"></a>행 집합 클래스

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)

여러 구현 인터페이스를 여러 번 상속 하지 않고도 표준 OLE DB 행 집합 구현을 제공 합니다. 구현을 제공 해야 하는 유일한 방법은 `Execute` 입니다.

[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
클래스에서 사용 되는 행 핸들의 기본 구현을 제공 합니다 `IRowsetImpl` . 행 핸들은 논리적으로 결과 행에 대 한 고유 태그입니다. `IRowsetImpl``CSimpleRow`에서 요청 된 모든 행에 대해 새를 만듭니다 `IRowsetImpl::GetNextRows` .

[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB에서는 공급자가 `HACCESSOR` 구조체의 배열에 대 한 태그란를 구현 해야 합니다 `DBBINDING` . `HACCESSOR`는 구조체의 주소인를 제공 `BindType` 합니다. 행 집합 및 명령에 대해 필수입니다.

[IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
공급자 열 맵에 의해 정의 된 정적 함수에 위임 합니다. 행 집합 및 명령의 필수 인터페이스입니다.

[IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)<br/>
명령 또는 행 집합에 대 한 형식 변환의 가용성에 대 한 정보를 제공 합니다. 명령, 행 집합 및 인덱스 행 집합에 대해 필수입니다. `IConvertType`OLE DB에서 제공 하는 변환 개체에 위임 하 여 인터페이스를 구현 합니다.

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
`IDBSchemaRowset`인터페이스 및 템플릿 화 creator 함수를 구현 `CreateSchemaRowset` 합니다.

[IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)<br/>
단일 기본 테이블이 나 인덱스의 모든 행을 포함 하는 행 집합을 열고 반환 합니다. 세션 개체에 대 한 필수 인터페이스입니다.

[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
기존 행의 열 값을 업데이트 하 고, 행을 삭제 하 고, 새 행을 삽입할 수 있도록 하는 OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) 인터페이스를 구현 합니다.

[IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
이 클래스는 [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) 에서 상속 되며 [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)를 재정의 합니다. `IRowsetCreatorImpl` 와 동일한 기능을 수행 하 `IObjectWithSite` 고 OLE DB 속성과도 사용 하도록 설정 합니다 `DBPROPCANSCROLLBACKWARDS` `DBPROPCANFETCHBACKWARDS` .

[IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)<br/>
`IRowsetIdentity`두 데이터 행이 동일한 지 여부를 비교할 수 있는 인터페이스를 구현 합니다.

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
`IRowset`기본 행 집합 인터페이스인 인터페이스의 구현을 제공 합니다.

[IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)<br/>
명령 클래스에 정의 된 속성 집합 맵을 사용 하 여 행 집합 속성을 구현 합니다. 행 집합의 필수 인터페이스입니다.

[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
행 집합에서 임의 행을 인출 하는 OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) 인터페이스를 구현 합니다. 행 집합에서 책갈피 OLE DB을 지원 하려면 행 집합이이 클래스에서 상속 하도록 합니다.

[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
는 행 집합 내용에 대 한 변경 내용의 연결 지점에 수신기를 알리기 위해 브로드캐스트 함수를 구현 `IID_IRowsetNotify` 합니다. 알림을 처리 하는 소비자는 [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) 를 구현 하 고 해당 연결 지점에 등록 합니다.

[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) 인터페이스를 OLE DB 구현 합니다 .이 인터페이스를 사용 하면 소비자가 [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) 를 사용 하 여 변경한 내용을 데이터 원본으로 전송 하 고 전송 전에 변경 내용을 실행 취소할 수 있습니다.

## <a name="command-classes"></a>명령 클래스

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
`ICommand` 인터페이스의 구현을 제공합니다. 이 인터페이스는 표시 되지 않지만에서 처리 됩니다 `ICommandTextImpl` . Command 개체의 필수 인터페이스입니다.

[ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
이 `ICommandProperties` 인터페이스 구현은 매크로에서 정의한 정적 함수를 통해 제공 됩니다 `BEGIN_PROPSET_MAP` . 필수 명령입니다.

[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
명령 텍스트를 설정, 저장 및 반환 합니다. 필수 명령입니다.

[IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
Session 개체에서 새 명령을 만들고 새로 만든 명령에 요청 된 인터페이스를 반환 합니다. 세션 개체에 대 한 선택적 인터페이스입니다.

다른 명령 클래스는 `IColumnsInfoImpl` `IAccessorImpl` 위의 행 집합 클래스 섹션에 설명 된 및입니다.

## <a name="data-source-classes"></a>데이터 원본 클래스

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
소비자와의 연결을 만들고 삭제 합니다. 데이터 원본 개체에 대 한 필수 인터페이스 및 열거자의 선택적 인터페이스

[IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` 는 데이터 원본 개체에 대 한 필수 인터페이스 이며 열거자에 대 한 선택적 인터페이스입니다. 그러나 열거자가를 노출 하는 경우 `IDBInitialize` `IDBProperties` (데이터 소스의 속성)를 노출 해야 합니다.

[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)<br/>
데이터 소스 개체에 대 한 인터페이스 포인터를 가져옵니다. 세션에 대 한 필수 인터페이스입니다.

## <a name="other-classes"></a>기타 클래스

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
다양 한 OLE DB 속성 인터페이스 (예:, 및)에 대 한 속성을 구현 `IDBProperties` `ISessionProperties` `IRowsetInfo` 합니다.

[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)

데이터 멤버에서 레코드를 추가 하 고 검색 하는 OLE DB [Ierrorrecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) 인터페이스를 구현 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB 템플릿](../../data/oledb/ole-db-templates.md)
