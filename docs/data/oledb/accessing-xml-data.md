---
title: XML 데이터 액세스
ms.date: 10/18/2018
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
ms.openlocfilehash: 437f1d103420ec5727294894c02587c68cffbdda
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509130"
---
# <a name="accessing-xml-data"></a>XML 데이터 액세스

데이터 원본에서 XML 데이터를 검색 하는 방법에는 두 가지가 있습니다. 하나는 [CStreamRowset](../../data/oledb/cstreamrowset-class.md) 을 사용 하 고 다른 하나는 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)를 사용 합니다.

|기능|CStreamRowset|CXMLAccessor|
|-------------------|-------------------|------------------|
|전송 된 데이터의 양|모든 열과 행에서 한 번에 데이터를 검색 합니다.|모든 열에서 데이터를 검색 하지만 한 번에 한 행씩 검색 합니다. 와 같은 메서드를 사용 하 여 행을 탐색 해야 합니다 `MoveNext` .|
|문자열 서식 지정|SQL Server XML 문자열의 형식을 지정 하 고 소비자에 게 보냅니다.|원시 형식으로 행 집합 데이터를 검색 한 다음 (공급자가 유니코드 문자열로 전송 하도록 요청) XML 형식으로 데이터를 포함 하는 문자열을 작성 합니다.|
|서식 지정 제어|일부 SQL Server 2000 관련 속성을 설정 하 여 XML 문자열의 형식을 지정 하는 방법을 제어할 수 있습니다.|생성 된 XML 문자열의 형식을 제어할 수 없습니다.|

는 `CStreamRowset` XML 형식으로 데이터를 검색 하는 보다 전체 효율적인 방법을 제공 하지만 SQL Server 2000 에서만 지원 됩니다.

## <a name="retrieving-xml-data-using-cstreamrowset"></a>CStreamRowset를 사용 하 여 XML 데이터 검색

또는 선언의 행 집합 형식으로 [CStreamRowset](../../data/oledb/cstreamrowset-class.md) 를 지정 `CCommand` `CTable` 합니다. 접근자를 사용 하거나 접근자를 사용 하지 않고 사용할 수 있습니다. 예를 들면 다음과 같습니다.

```cpp
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;
```

또는

```cpp
CCommand<CNoAccessor, CStreamRowset> myCmd;
```

일반적으로를 호출 하는 경우 `CCommand::Open` (예: `CRowset` 클래스로 지정 `TRowset` ) 포인터를 가져옵니다 `IRowset` . `ICommand::Execute``IRowset`개체의 멤버에 저장 된 포인터를 반환 합니다 `m_spRowset` `CRowset` . , 및와 같은 메서드 `MoveFirst` `MoveNext` `GetData` 는 해당 포인터를 사용 하 여 데이터를 검색 합니다.

반면를 호출 하는 경우 `CCommand::Open` (를 `CStreamRowset` 클래스로 지정)는 `TRowset` `ICommand::Execute` `ISequentialStream` `m_spStream` [CStreamRowset](../../data/oledb/cstreamrowset-class.md)의 데이터 멤버에 저장 된 포인터를 반환 합니다. 그런 다음 메서드를 사용 `Read` 하 여 XML 형식의 (유니코드 문자열) 데이터를 검색 합니다. 다음은 그 예입니다.

```cpp
myCmd.m_spStream->Read()
```

SQL Server 2000은 XML 서식 지정을 수행 하 고 행 집합의 모든 열과 모든 행을 하나의 XML 문자열로 반환 합니다.

메서드를 사용 하는 예제는 `Read` [간단한 소비자 구현](../../data/oledb/implementing-a-simple-consumer.md)에서 **소비자에 게 XML 지원 추가** 를 참조 하세요.

> [!NOTE]
> 을 사용 하는 XML 지원은 `CStreamRowset` SQL Server 2000에만 사용할 수 있으며, SQL Server 2000 용 OLE DB 공급자 (MDAC와 함께 설치 됨)가 있어야 합니다.

## <a name="retrieving-xml-data-using-cxmlaccessor"></a>CXMLAccessor를 사용 하 여 XML 데이터 검색

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) 를 사용 하면 데이터 저장소의 스키마에 대해 알지 못하는 경우 데이터 원본의 데이터를 문자열 데이터로 액세스할 수 있습니다. `CXMLAccessor` 는와 같이 작동 합니다 `CDynamicStringAccessorW` . 단,는 데이터 저장소에서 액세스 되는 모든 데이터를 XML 형식 (태그가 지정 된) 데이터로 변환 합니다. XML 태그 이름은 데이터 저장소의 열 이름과 최대한 유사 하 게 일치 합니다.

`CXMLAccessor`다른 접근자 클래스와 같이를 사용 하 여 또는에 템플릿 매개 변수로 전달 합니다 `CCommand` `CTable` .

```cpp
CTable<CXMLAccessor, CRowset> rs;
```

[Getxmlrowdata](./cxmlaccessor-class.md#getxmlrowdata) 를 사용 하 여 테이블에서 한 번에 한 행씩 데이터를 검색 하 고와 같은 메서드를 사용 하 여 행을 탐색할 수 `MoveNext` 있습니다. 예를 들면 다음과 같습니다.

```cpp
// Open data source, session, and rowset
hr = rs.MoveFirst();

while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
{
    CStringW strRowData;
    myCmd.GetXMLRowData(strRowData);

    printf_s( "%S\n", strRowData );

    hr = rs.MoveNext();
}
```

[Getxmlcolumndata](./cxmlaccessor-class.md#getxmlcolumndata) 를 사용 하 여 열 (데이터 형식) 정보를 XML 형식의 문자열 데이터로 검색할 수 있습니다.

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)
