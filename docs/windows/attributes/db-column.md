---
title: db_column (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_column
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
ms.openlocfilehash: 2828a33a31d806c04cfce76a3156674778efbe6e
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686485"
---
# <a name="db_column"></a>db_column

지정 된 열을 행 집합의 변수에 바인딩합니다.

## <a name="syntax"></a>구문

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>매개 변수

*순서로*<br/>
`DBCOLUMNINFO`데이터를 바인딩할 행 집합의 필드에 해당 하는 서 수 열 번호 (서 수) 또는 열 이름 (ANSI 또는 유니코드 문자열)입니다. 숫자를 사용 하는 경우 연속 서 수를 건너뛸 수 있습니다 (예: 1, 2, 3, 5). 사용 하는 OLE DB 공급자가 지 원하는 경우 이름에 공백이 포함 될 수 있습니다. 예를 들어, 다음 형식 중 하나를 사용할 수 있습니다.

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

*dbtype*<br/>
필드 열 항목에 대 한 OLE DB [형식 표시기](/previous-versions/windows/desktop/ms711251(v=vs.85)) 입니다.

*전체 자릿수*<br/>
필드 열 항목에 사용할 전체 자릿수입니다. 자세한 내용은 `bPrecision` [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85)) 의 요소에 대 한 설명을 참조 하세요.

*scale*<br/>
필드 열 항목에 사용할 소수 자릿수입니다. 자세한 내용은 `bScale` [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85)) 의 요소에 대 한 설명을 참조 하세요.

*status*<br/>
필드 이 열의 상태를 유지 하는 데 사용 되는 멤버 변수입니다. 상태는 열 값이 데이터 값 인지 아니면 다른 값 (예: NULL) 인지를 나타냅니다. 가능한 값은 *OLE DB 프로그래머 참조*의 [상태](/previous-versions/windows/desktop/ms722617(v=vs.85)) 를 참조 하세요.

*length*<br/>
필드 열 크기를 저장 하는 데 사용 되는 멤버 변수 (바이트)입니다.

## <a name="remarks"></a>설명

지정 된 테이블 열을 행 집합의 변수에 **db_column** 바인딩합니다. OLE DB 기반 바인딩에 참여할 수 있는 멤버 데이터를 구분 `IAccessor` 합니다. 이 특성은 OLE DB consumer 매크로 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../../data/oledb/end-column-map.md)및 [COLUMN_ENTRY](../../data/oledb/column-entry.md)를 사용 하 여 일반적으로 정의 된 열 맵을 설정 합니다. 이러한 OLE DB [DBBINDING 구조체](/previous-versions/windows/desktop/ms716845(v=vs.85)) 를 조작 하 여 지정 된 열을 바인딩합니다. **Db_column** 특성으로 표시 하는 각 멤버는 열 맵의 한 항목을 열 항목의 형식으로 사용 합니다. 따라서이 특성은 명령 또는 테이블 클래스에서 열 맵을 배치 하는 곳에 호출 합니다.

[Db_table](db-table.md) 또는 [db_command](db-command.md) 특성과 함께 **db_column** 를 사용 합니다.

소비자 특성 공급자가 클래스에 이 특성을 적용하는 경우 컴파일러는 클래스의 이름을 _\_*YourClassName*Accessor로 바꿉니다. 여기서 *YourClassName*은 클래스에 지정한 이름입니다. 컴파일러는 또한 \_*YourClassName*Accessor에서 파생되는 *YourClassName*이라는 클래스를 만듭니다.  클래스 뷰에 두 클래스 모두 표시됩니다.

응용 프로그램에서 사용 되는이 특성의 예는 [Multiread](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)를 참조 하세요.

## <a name="examples"></a>예제

이 샘플은 테이블의 열을 **`long`** 데이터 멤버에 바인딩하고 상태 및 길이 필드를 지정 합니다.

```cpp
// db_column_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   DBSTATUS m_dwProductIDStatus;
   DBLENGTH m_dwProductIDLength;

   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;
};
```

이 샘플에서는 네 개의 열을 **`long`** , 문자열, 타임 스탬프 및 `DB_NUMERIC` 정수로 바인딩합니다.

```cpp
// db_column_2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   [db_column("1")] LONG m_OrderID;
   [db_column("2")] TCHAR m_CustomerID[6];
   [db_column("4")] DB_NUMERIC m_OrderDate;
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`** , 멤버, 메서드|
|**불가능**|No|
|**필수 특성**|None|
|**잘못된 특성**|None|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>추가 정보

[OLE DB 소비자 특성](ole-db-consumer-attributes.md)<br/>
[클래스 특성](class-attributes.md)
