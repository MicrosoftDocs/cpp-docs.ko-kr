---
description: '자세히 알아보기: CXMLAccessor 클래스'
title: CXMLAccessor 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
- ATL.CXMLAccessor.GetXMLColumnData
- CXMLAccessor::GetXMLColumnData
- CXMLAccessor.GetXMLColumnData
- ATL::CXMLAccessor::GetXMLColumnData
- GetXMLColumnData
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
helpviewer_keywords:
- CXMLAccessor class
- GetXMLColumnData method
- GetXMLRowData method
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
ms.openlocfilehash: 30725f47add9f9b965fe36226a366342988275e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287699"
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor 클래스

데이터 저장소의 스키마 (기본 구조)에 대해 알지 못하는 경우 데이터 원본에 문자열 데이터를 액세스할 수 있습니다.

## <a name="syntax"></a>Syntax

```cpp
class CXMLAccessor : public CDynamicStringAccessorW
```

## <a name="requirements"></a>요구 사항

**헤더**: atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[GetXMLColumnData](#getxmlcolumndata)|열 정보를 검색 합니다.|
|[GetXMLRowData](#getxmlrowdata)|행을 기준으로 테이블의 전체 내용을 검색 합니다.|

## <a name="remarks"></a>설명

그러나 `CXMLAccessor` `CDynamicStringAccessorW` 는 데이터 저장소에서 액세스 되는 모든 데이터를 XML 형식 (태그가 지정 된) 데이터로 변환 한다는 점에서와 다릅니다. 이는 XML 인식 웹 페이지의 출력에 특히 유용 합니다. XML 태그 이름은 데이터 저장소의 열 이름과 최대한 유사 하 게 일치 합니다.

`CDynamicAccessor`메서드를 사용 하 여 열 정보를 가져올 수 있습니다. 이 열 정보를 사용 하 여 런타임에 동적으로 접근자를 만들 수 있습니다.

열 정보는이 클래스에서 만들고 관리 하는 버퍼에 저장 됩니다. [Getxmlcolumndata](#getxmlcolumndata) 를 사용 하 여 열 정보를 얻거나 [getxmlcolumndata](#getxmlrowdata)를 사용 하 여 행으로 열 데이터를 가져옵니다.

## <a name="example"></a>예제

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="cxmlaccessorgetxmlcolumndata"></a><a name="getxmlcolumndata"></a> CXMLAccessor:: GetXMLColumnData

열을 기준으로 테이블의 열 형식 정보를 XML 형식의 문자열 데이터로 검색 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>매개 변수

*strOutput*<br/>
제한이 검색할 열 형식 정보를 포함 하는 문자열 버퍼에 대 한 참조입니다. 문자열은 데이터 저장소의 열 이름과 일치 하는 XML 태그 이름을 사용 하 여 형식이 지정 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

다음에서는 XML로 열 형식 정보의 형식을 지정 하는 방법을 보여 줍니다. `type` 열의 데이터 형식을 지정 합니다. 데이터 형식은 OLE DB 데이터 형식에 기반을 두고 있으며 액세스 되는 데이터베이스의 데이터 형식에는 사용 되지 않습니다.

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="cxmlaccessorgetxmlrowdata"></a><a name="getxmlrowdata"></a> CXMLAccessor:: GetXMLRowData

테이블의 전체 내용을 행별로 XML 형식의 문자열 데이터로 검색 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>매개 변수

*strOutput*<br/>
제한이 검색할 테이블 데이터를 포함 하는 버퍼에 대 한 참조입니다. 데이터는 데이터 저장소의 열 이름과 일치 하는 XML 태그 이름을 사용 하 여 문자열 데이터로 서식 지정 됩니다.

*bAppend*<br/>
진행 출력 데이터의 끝에 문자열을 추가할지 여부를 지정 하는 부울 값입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

다음은 행 데이터의 형식을 XML로 지정 하는 방법을 보여 줍니다. `DATA` 다음은 행 데이터를 나타냅니다. Move 메서드를 사용 하 여 원하는 행으로 이동 합니다.

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 클래스](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor 클래스](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor 클래스](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor 클래스](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA 클래스](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW 클래스](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor 클래스](../../data/oledb/cmanualaccessor-class.md)
