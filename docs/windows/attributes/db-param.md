---
description: '다음에 대 한 자세한 정보: db_param'
title: db_param (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_param
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
ms.openlocfilehash: 27666b4cdf027e24b54326a3acc5fe701b9f6f44
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333112"
---
# <a name="db_param"></a>db_param

지정 된 멤버 변수를 입력 또는 출력 매개 변수와 연결 하 고 변수를 구분 합니다.

## <a name="syntax"></a>구문

```cpp
[ db_param(ordinal, paramtype="DBPARAMIO_INPUT", dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>매개 변수

*순서로*<br/>
데이터를 바인딩할 행 집합의 필드에 해당 하는 열 번호 (DBCOLUMNINFO ordinal)입니다.

*가 paramtype과*<br/>
필드 매개 변수에 대해 설정할 형식입니다. 공급자는 기본 데이터 소스에서 지원 되는 매개 변수 i/o 유형만 지원 합니다. 형식은 하나 이상의 DBPARAMIOENUM 값의 조합입니다.

- DBPARAMIO_INPUT 입력 매개 변수입니다.

- DBPARAMIO_OUTPUT 출력 매개 변수입니다.

- DBPARAMIO_NOTPARAM 이 접근자에는 매개 변수가 없습니다. `eParamIO`행 접근자에서이 값을로 설정 하면 매개 변수가 무시 됨을 사용자에 게 알립니다.

*dbtype*<br/>
필드 열 항목에 대 한 OLE DB [형식 표시기](/previous-versions/windows/desktop/ms711251(v=vs.85)) 입니다.

*전체 자릿수*<br/>
필드 열 항목에 사용할 전체 자릿수입니다. 자세한 내용은 `bPrecision` [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85)) 의 요소에 대 한 설명을 참조 하세요.

*scale*<br/>
필드 열 항목에 사용할 소수 자릿수입니다. 자세한 내용은 `bScale` [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85)) 의 요소에 대 한 설명을 참조 하세요.

*status*<br/>
필드 이 열의 상태를 유지 하는 데 사용 되는 멤버 변수입니다. 상태는 열 값이 데이터 값 인지 아니면 다른 값 (예: NULL) 인지를 나타냅니다. 가능한 값은 *OLE DB 프로그래머 참조* 의 [상태](/previous-versions/windows/desktop/ms722617(v=vs.85)) 를 참조 하세요.

*length*<br/>
필드 열 크기를 저장 하는 데 사용 되는 멤버 변수 (바이트)입니다.

## <a name="remarks"></a>설명

**db_param** 명령에서 사용 하는 매개 변수를 정의 합니다. 따라서와 함께 사용 `db_command` 합니다. 예를 들어 **db_param** 를 사용 하 여 SQL 쿼리 또는 저장 프로시저에서 매개 변수를 바인딩할 수 있습니다. 저장 프로시저의 매개 변수는 물음표 (?)로 표시 되며, 매개 변수가 표시 되는 순서 대로 데이터 멤버를 바인딩해야 합니다.

**db_param** 는 OLE DB 기반 바인딩에 참여할 수 있는 멤버 데이터를 구분 `ICommandWithParameters` 합니다. 지정 된 매개 변수에 대 한 매개 변수 형식 (입력 또는 출력), OLE DB 형식, 전체 자릿수, 소수 자릿수, 상태 및 길이를 설정 합니다. 이 특성은 BEGIN_PARAM_MAP OLE DB 소비자 매크로를 삽입 합니다. END_PARAM_MAP. **Db_param** 특성으로 표시 하는 각 멤버는 맵의 한 항목을 COLUMN_ENTRY 형식으로 사용 합니다.

**db_param** 은 [db_table](db-table.md) 또는 [db_command](db-command.md) 특성과 함께 사용 됩니다.

소비자 특성 공급자가 클래스에 이 특성을 적용하는 경우 컴파일러는 클래스의 이름을 _\_*YourClassName* Accessor로 바꿉니다. 여기서 *YourClassName* 은 클래스에 지정한 이름입니다. 컴파일러는 또한 \_*YourClassName* Accessor에서 파생되는 *YourClassName* 이라는 클래스를 만듭니다.  클래스 뷰에 두 클래스 모두 표시됩니다.

## <a name="example"></a>예제

다음 예에서는 Northwind 데이터베이스의 SalesbyYear 저장 프로시저를 기반으로 하는 명령 클래스를 만듭니다. 저장 프로시저의 첫 번째 매개 변수를 변수와 연결 하 `m_RETURN_VALUE` 고 출력 매개 변수로 정의 합니다. 마지막 두 개의 (입력) 매개 변수를 및에 연결 합니다 `m_Beginning_Date` `m_Ending_Date` .

다음 예에서는 변수를 `nOutput` output 매개 변수와 연결 합니다.

```cpp
// db_param.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_source(L"my_connection_string"),
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")
]
struct CSalesbyYear {
   DBSTATUS m_dwShippedDateStatus;
   DBSTATUS m_dwOrderIDStatus;
   DBSTATUS m_dwSubtotalStatus;
   DBSTATUS m_dwYearStatus;

   DBLENGTH m_dwShippedDateLength;
   DBLENGTH m_dwOrderIDLength;
   DBLENGTH m_dwSubtotalLength;
   DBLENGTH m_dwYearLength;

   // Bind columns
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];

   // Bind parameters
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`** , 멤버, 메서드, 로컬|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 특성](ole-db-consumer-attributes.md)
