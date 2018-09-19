---
title: db_source | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c43139dd1d927d9e6173d9e78765d0fcdbddae6a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716016"
---
# <a name="dbsource"></a>db_source

데이터 원본에 연결을 만듭니다.

## <a name="syntax"></a>구문

```cpp
[ db_source(
   db_source,
   name,
   hresult
) ]
```

### <a name="parameters"></a>매개 변수

*db_source*  
데이터 원본에 연결할 때 사용할 연결 문자열입니다. 연결 문자열의 형식에 대해서 [연결 문자열 및 데이터 링크](/previous-versions/windows/desktop/ms718376\(v=vs.85\)) 에 Microsoft 데이터 액세스 구성 요소 (MDAC) SDK입니다.

*name*  
(선택 사항) 사용 하는 경우 **db_source** 클래스에서 *이름* 있는 데이터 원본 개체의 인스턴스를 **db_source** 특성 (예 1 참조)를 적용 합니다. 사용 하는 경우 **db_source** 메서드 구현에서 인라인 *이름* 데이터 액세스에 사용할 수 있는 변수 (로컬 메서드에) 원본 (예 2 참조). 이 전달할 *이름* 에 *source_name* 의 매개 변수 `db_command` 명령을 사용 하 여 데이터 원본에 연결할 합니다.

*hresult*  
(선택 사항) 이 데이터베이스 명령의 HRESULT 받을 변수를 식별 합니다. 변수가 없으면 특성에 의해 자동으로 삽입됩니다.

## <a name="remarks"></a>설명

**db_source** 만듭니다는 [CDataSource](../data/oledb/cdatasource-class.md) 와 [CSession](../data/oledb/csession-class.md) OLE DB 소비자 데이터 원본 사용 하 여 연결을 나타내는 개체입니다.

사용 하는 경우 **db_source** 클래스에는 `CSession` 개체 클래스의 멤버가 됩니다.

사용 하는 경우 **db_source** 메서드에서 삽입된 된 코드 메서드 범위 내에서 실행 되므로 및 `CSession` 지역 변수로 개체가 만들어집니다.

**db_source** 클래스 또는 메서드 내에서 데이터 원본 속성을 추가 합니다. 와 함께에서 사용 됩니다 `db_command` (사용 하는 합니다 *db_source* *이름* 매개 변수에 해당 *source_name* 매개 변수).

컴파일러는 클래스 이름을 소비자 특성 공급자가이 특성 클래스에 적용 될 때 \_ *YourClassName*접근자를 여기서 *YourClassName* 제공한 이름인는 클래스 및 컴파일러 라는 클래스를 만들 수도 됩니다 *YourClassName*에서 파생 되는 \_ *YourClassName*접근자입니다.  클래스 뷰에 두 클래스 모두 표시됩니다.

응용 프로그램에서 사용 되는이 특성의 예로, 샘플을 참조 하세요 [AtlAgent](https://github.com/Microsoft/VCSamples) 하 고 [MultiRead](https://github.com/Microsoft/VCSamples)합니다.

## <a name="example"></a>예제

이 샘플에서는 호출 **db_source** 데이터 원본에 대 한 연결을 만들려면 클래스에 `ds` Northwind 데이터베이스를 사용 합니다. `ds` 내부적으로 사용할 수 있는 데이터 원본에 대 한 핸들을 `CMyCommand` 클래스입니다.

```cpp
// db_source_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[
  db_source(L"my_connection_string", name="ds"),
  db_command(L"select * from Products")  
]
class CMyCommand {};
```

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|**클래스**하십시오 **구조체**, 멤버, 메서드, 로컬|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](../windows/attribute-contexts.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 특성](../windows/ole-db-consumer-attributes.md)  
