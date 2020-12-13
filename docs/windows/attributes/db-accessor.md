---
description: '다음에 대 한 자세한 정보: db_accessor'
title: db_accessor (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: b32fb16fe938a84280b0fb047923bbc2aa687c75
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333115"
---
# <a name="db_accessor"></a>db_accessor

`db_column`기반 바인딩에 참여 하는 특성을 그룹화 `IAccessor` 합니다.

## <a name="syntax"></a>구문

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>매개 변수

*num*<br/>
접근자 번호 (0부터 시작 하는 정수 인덱스)를 지정 합니다. 정수 또는 정의 된 값을 사용 하 여 오름차순으로 접근자 번호를 지정 해야 합니다.

*auto*<br/>
접근자가 자동으로 검색 되는지 (TRUE) 또는 검색 되지 않는지 (FALSE)를 지정 하는 부울 값입니다.

## <a name="remarks"></a>설명

**db_accessor** 는 `db_column` `db_param` 동일한 클래스 또는 함수 내의 후속 및 특성에 대 한 기본 OLE DB 접근자를 정의 합니다. **db_accessor** 은 멤버 수준에서 사용할 수 있으며 `db_column` OLE DB 기반 바인딩에 참여 하는 특성을 그룹화 하는 데 사용 됩니다 `IAccessor` . 또는 특성과 함께 사용 됩니다 `db_table` `db_command` . 이 특성을 호출 하는 것은 [BEGIN_ACCESSOR](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor) 및 [END_ACCESSOR](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md#end_accessor) 매크로를 호출 하는 것과 비슷합니다.

**db_accessor** 는 행 집합을 생성 하 고 해당 접근자 맵에 바인딩합니다. **Db_accessor** 를 호출 하지 않으면 접근자 0이 자동으로 생성 되 고 모든 열 바인딩이이 접근자 블록에 매핑됩니다.

**db_accessor** 는 데이터베이스 열 바인딩을 하나 이상의 접근자로 그룹화 합니다. 여러 접근자를 사용 해야 하는 시나리오에 대 한 설명은 [행 집합에서 여러 접근자 사용](../../data/oledb/using-multiple-accessors-on-a-rowset.md)을 참조 하세요. [사용자 레코드](../../data/oledb/user-records.md)에서 "여러 접근자에 대 한 사용자 레코드 지원"도 참조 하세요.

소비자 특성 공급자가 클래스에 이 특성을 적용하는 경우 컴파일러는 클래스의 이름을 _\_*YourClassName* Accessor로 바꿉니다. 여기서 *YourClassName* 은 클래스에 지정한 이름입니다. 컴파일러는 또한 \_*YourClassName* Accessor에서 파생되는 *YourClassName* 이라는 클래스를 만듭니다.  클래스 뷰에 두 클래스 모두 표시됩니다.

## <a name="example"></a>예제

다음 예에서는 **db_accessor** 를 사용 하 여 Orders 테이블의 열을 Northwind 데이터베이스에서 두 개의 접근자로 그룹화 합니다. 접근자 0은 자동 접근자 이며 접근자 1은 그렇지 않습니다.

```cpp
// cpp_attr_ref_db_accessor.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include <atlbase.h>
#include <atldbcli.h>

[ db_command(L"SELECT LastName, FirstName FROM Orders") ]
class CEmployees {
public:
   [ db_accessor(0, TRUE) ];
   [ db_column("1") ] LONG m_OrderID;
   [ db_column("2") ] TCHAR m_CustomerID[6];
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;

   [ db_accessor(1, FALSE) ];
   [ db_column("8") ] CURRENCY m_Freight;
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|특성 블록|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 특성](ole-db-consumer-attributes.md)
