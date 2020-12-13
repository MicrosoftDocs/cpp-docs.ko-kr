---
description: '다음에 대 한 자세한 정보: db_table'
title: db_table (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_table
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
ms.openlocfilehash: 3d871961a8ded6070127e5e562615018a4320162
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333049"
---
# <a name="db_table"></a>db_table

OLE DB 테이블을 엽니다.

## <a name="syntax"></a>구문

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

### <a name="parameters"></a>매개 변수

*db_table*<br/>
데이터베이스 테이블의 이름을 지정 하는 문자열입니다 (예: "Products").

*name*<br/>
필드 테이블 작업에 사용 하는 핸들의 이름입니다. 결과 행을 두 개 이상 반환 하려면이 매개 변수를 지정 해야 합니다. **db_table** 행 집합을 트래버스 하거나 여러 작업 쿼리를 실행 하는 데 사용할 수 있는 지정 된 *이름의* 변수를 생성 합니다.

*source_name*<br/>
(선택 사항) `CSession` 특성이 적용되어 명령이 실행되는 클래스의 `db_source` 변수 또는 인스턴스. [db_source](db-source.md)를 참조하세요.

*hresult*<br/>
(선택 사항) 이 데이터베이스 명령의 HRESULT를 수신할 변수를 식별합니다. 변수가 없으면 특성에 의해 자동으로 삽입됩니다.

## <a name="remarks"></a>설명

**db_table** 는 OLE DB 소비자가 테이블을 여는 데 사용 하는 [CTable](../../data/oledb/ctable-class.md) 개체를 만듭니다. 이 특성은 클래스 수준 에서만 사용할 수 있습니다. 인라인에서는 사용할 수 없습니다. `db_column`를 사용 하 여 테이블 열을 변수에 바인딩한 다음를 사용 하 여 `db_param` 매개 변수 형식을 구분 (설정) 합니다.

소비자 특성 공급자가 클래스에 이 특성을 적용하는 경우 컴파일러는 클래스의 이름을 _\_*YourClassName* Accessor로 바꿉니다. 여기서 *YourClassName* 은 클래스에 지정한 이름입니다. 컴파일러는 또한 \_*YourClassName* Accessor에서 파생되는 *YourClassName* 이라는 클래스를 만듭니다.  클래스 뷰에 두 클래스 모두 표시됩니다.

## <a name="example"></a>예제

다음 예에서는에서 사용할 Products 테이블을 엽니다 `CProducts` .

```cpp
// db_table.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_table(L"dbo.Products") ]
class CProducts {
   [ db_column("1") ] LONG m_ProductID;
};
```

응용 프로그램에서 사용 되는이 특성의 예는 [Multiread](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)를 참조 하세요.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`**|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 특성](ole-db-consumer-attributes.md)
