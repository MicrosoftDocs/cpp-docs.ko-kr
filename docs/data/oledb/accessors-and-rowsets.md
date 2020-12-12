---
description: '다음에 대 한 자세한 정보: 접근자 및 행 집합'
title: 접근자 및 행 집합
ms.date: 11/19/2018
helpviewer_keywords:
- accessors [C++]
- OLE DB consumer templates, rowset support
- OLE DB consumer templates, accessors
- rowsets [C++], accessing
- bulk rowsets
- CAccessorRowset class, accessor types
- single rowsets
- CArrayRowset class, accessors
- CBulkRowset class, accessors
- array rowsets
- CAccessorBase class
- CRowset class, accessors and rowsets
- accessors [C++], rowsets
- rowsets [C++], supported types
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
ms.openlocfilehash: 5bda7957f808319de596edf51b6cb3e378c14254
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246112"
---
# <a name="accessors-and-rowsets"></a>접근자 및 행 집합

데이터를 설정 하 고 검색 하려면 OLE DB 템플릿에서 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) 클래스를 통해 접근자와 행 집합을 사용 합니다. 이 클래스는 다른 형식의 여러 접근자를 처리할 수 있습니다.

## <a name="accessor-types"></a>접근자 형식

모든 접근자는 [CAccessorBase](../../data/oledb/caccessorbase-class.md)에서 파생 됩니다. `CAccessorBase` 는 매개 변수와 열 바인딩을 모두 제공 합니다.

다음 그림에서는 접근자 형식을 보여 줍니다.

![접근자 형식](../../data/oledb/media/vcaccessortypes.gif "접근자 형식")<br/>
접근자 클래스

- [CAccessor](../../data/oledb/caccessor-class.md) 디자인 타임에 데이터베이스 원본의 구조를 알고 있는 경우이 접근자를 사용 합니다. `CAccessor` 버퍼를 포함 하는 데이터베이스 레코드를 데이터 소스에 정적으로 바인딩합니다.

- [Cdynamicaccessor](../../data/oledb/cdynamicaccessor-class.md) 디자인 타임에 데이터베이스의 구조를 모르는 경우이 접근자를 사용 합니다. `CDynamicAccessor``IColumnsInfo::GetColumnInfo`을 호출 하 여 데이터베이스 열 정보를 가져옵니다. 접근자와 버퍼를 만들고 관리 합니다.

- [Cdynamicparameteraccessor](../../data/oledb/cdynamicparameteraccessor-class.md) 이 접근자를 사용 하 여 알 수 없는 명령 유형을 처리 합니다. 명령을 준비할 때는 공급자가를 `CDynamicParameterAccessor` `ICommandWithParameters` 지 원하는 경우 인터페이스에서 매개 변수 정보를 가져올 수 있습니다 `ICommandWithParameters` .

- [Cdynamicstringaccessor](../../data/oledb/cdynamicstringaccessor-class.md), [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)및 [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md) 는 데이터베이스 스키마에 대해 알지 못하는 경우 이러한 클래스를 사용 합니다. `CDynamicStringAccessorA` 데이터를 ANSI 문자열로 검색 합니다. `CDynamicStringAccessorW` 데이터를 유니코드 문자열로 검색 합니다.

- [CManualAccessor](../../data/oledb/cmanualaccessor-class.md) 이 클래스를 사용 하면 공급자가 형식을 변환할 수 있는 경우 원하는 모든 데이터 형식을 사용할 수 있습니다. 결과 열과 명령 매개 변수를 모두 처리 합니다.

다음 표에는 OLE DB 템플릿 접근자 형식의 지원이 요약 되어 있습니다.

|접근자 형식|동적|매개 변수 처리|Buffer|여러 접근자|
|-------------------|-------------|--------------------|------------|------------------------|
|`CAccessor`|아니요|예|사용자|예|
|`CDynamicAccessor`|예|아니요|OLE DB 템플릿|아니요|
|`CDynamicParameterAccessor`|예|예|OLE DB 템플릿|아니요|
|`CDynamicStringAccessor[A,W]`|예|아니요|OLE DB 템플릿|아니요|
|`CManualAccessor`|예|예|사용자|예|

## <a name="rowset-types"></a>행 집합 형식

OLE DB 템플릿은 세 종류의 행 집합을 지원 합니다 (이전 그림 참조). 단일 행 집합 ( [CRowset](../../data/oledb/crowset-class.md)에 의해 구현 됨), 대량 행 집합 ( [c대량 행 집합](../../data/oledb/cbulkrowset-class.md)으로 구현 됨) 및 배열 행 집합 ( [cbulkrowset](../../data/oledb/carrayrowset-class.md)에서 구현 됨)을 지원 합니다. 단일 행 집합은가 호출 될 때 단일 행 핸들을 페치합니다 `MoveNext` . 대량 행 집합은 여러 행 핸들을 페치할 수 있습니다. 배열 행 집합은 배열 구문을 사용 하 여 액세스할 수 있는 행 집합입니다.

다음 그림에서는 행 집합 형식을 보여 줍니다.

![RowsetType 그래픽](../../data/oledb/media/vcrowsettypes.gif "RowsetType 그래픽")<br/>
행 집합 클래스

[스키마 행 집합](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) 은 데이터 저장소의 데이터에 액세스 하지 않고 대신 메타 데이터 라고 하는 데이터 저장소에 대 한 정보에 액세스 합니다. 스키마 행 집합은 일반적으로 컴파일 시간에 데이터베이스 구조가 알려지지 않으며 런타임에 가져와야 하는 상황에서 사용 됩니다.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)
