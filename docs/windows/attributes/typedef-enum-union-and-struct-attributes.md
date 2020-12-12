---
description: '자세히 알아보기: Typedef, Enum, Union 및 Struct 특성'
title: Typedef, Enum, Union 및 Struct 특성 (c + + COM)
ms.date: 10/02/2018
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
ms.openlocfilehash: 9f72f5ff45709287d31aa4da05b2569a0b37baff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327241"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Typedef, Enum, Union 및 Struct 특성

다음 특성은 [typedef](../../cpp/aliases-and-typedefs-cpp.md), [struct](../../cpp/struct-cpp.md)및 [enum](../../cpp/enumerations-cpp.md) c + + 키워드에 적용 됩니다.

### <a name="typedef"></a>형식 정의

|특성|설명|
|---------------|-----------------|
|[case](case-cpp.md)|에서 [switch_type](switch-type.md) 특성과 함께 사용 **`union`** 됩니다.|
|[재구성](custom-cpp.md)|사용자 고유의 특성을 정의할 수 있습니다.|
|[내보내기가](export.md)|데이터 구조가 .idl 파일에 배치 되도록 합니다.|
|[first_is](first-is.md)|전송할 첫 번째 배열 요소의 인덱스를 지정 합니다.|
|[helpcontext](helpcontext.md)|사용자가 도움말 파일에서이 요소에 대 한 정보를 볼 수 있는 컨텍스트 ID를 지정 합니다.|
|[helpfile](helpfile.md)|형식 라이브러리에 대 한 도움말 파일의 이름을 설정 합니다.|
|[helpstring](helpstring.md)|적용되는 요소를 설명하는 데 사용되는 문자열을 지정합니다.|
|[library_block](library-block.md)|.Idl 파일의 라이브러리 블록 안에 구문을 배치 합니다.|
|[ptr](ptr.md)|포인터를 전체 포인터로 지정 합니다.|
|[public](public-cpp-attributes.md)|Idl 파일에서 참조 되지 않는 경우에도 형식 라이브러리에 typedef를 넣습니다.|
|[ref](ref-cpp.md)|참조 포인터를 식별 합니다.|
|[switch_is](switch-is.md)|Union 멤버를 선택 하는 union 판별 역할을 하는 식 또는 식별자를 지정 합니다.|
|[switch_type](switch-type.md)|Union 판별으로 사용 되는 변수의 형식을 식별 합니다.|
|[unique](unique-cpp.md)|고유 포인터를 지정 합니다.|
|[wire_marshal](wire-marshal.md)|응용 프로그램별 데이터 형식 대신 전송에 사용 되는 데이터 형식을 지정 합니다.|

### <a name="enum"></a>enum

|특성|설명|
|---------------|-----------------|
|[재구성](custom-cpp.md)|사용자 고유의 특성을 정의할 수 있습니다.|
|[내보내기가](export.md)|데이터 구조가 .idl 파일에 배치 되도록 합니다.|
|[uuid](uuid-cpp-attributes.md)|클래스 또는 인터페이스의 고유 ID를 지정 합니다.|
|[v1_enum](v1-enum.md)|지정 된 열거형 형식이 16 비트 기본값이 아닌 32 비트 엔터티로 전송 되도록 지정 합니다.|

### <a name="union"></a>union

|특성|설명|
|---------------|-----------------|
|[재구성](custom-cpp.md)|사용자 고유의 특성을 정의할 수 있습니다.|
|[내보내기가](export.md)|데이터 구조가 .idl 파일에 배치 되도록 합니다.|
|[first_is](first-is.md)|전송할 첫 번째 배열 요소의 인덱스를 지정 합니다.|
|[last_is](last-is.md)|전송할 마지막 배열 요소의 인덱스를 지정 합니다.|
|[length_is](length-is.md)|전송할 배열 요소의 수를 지정 합니다.|
|[max_is](max-is.md)|유효한 배열 인덱스에 대 한 최대값을 지정 합니다.|
|[size_is](size-is.md)|크기가 지정 된 포인터에 대해 할당 된 메모리 크기, 크기가 지정 된 포인터에 대 한 포인터 크기 조정 및 단일 또는 다차원 배열을 지정 합니다.|
|[unique](unique-cpp.md)|고유 포인터를 지정 합니다.|
|[uuid](uuid-cpp-attributes.md)|클래스 또는 인터페이스의 고유 ID를 지정 합니다.|

### <a name="nonencapsulated-union"></a>캡슐화 되지 않은 공용 구조체

|특성|설명|
|---------------|-----------------|
|[ms_union](ms-union.md)|캡슐화 되지 않은 공용 구조체의 네트워크 데이터 표현 맞춤을 제어 합니다.|
|[no_injected_text](no-injected-text.md)|컴파일러가 특성 사용의 결과로 코드를 삽입 하지 않도록 합니다.|

### <a name="struct"></a>struct

|특성|설명|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|클래스가 집계를 지원함을 나타냅니다.|
|[집계](aggregates.md)|컨트롤이 대상 클래스를 집계 함을 나타냅니다.|
|[appobject](appobject.md)|Coclass를 전체 .exe 응용 프로그램과 연결 된 응용 프로그램 개체로 식별 하 고 coclass의 함수 및 속성을이 형식 라이브러리에서 전역적으로 사용할 수 있음을 나타냅니다.|
|[coclass](coclass.md)|ActiveX 컨트롤을 만듭니다.|
|[com_interface_entry](com-interface-entry-cpp.md)|인터페이스 항목을 COM 맵에 추가 합니다.|
|[control](control.md)|사용자 정의 형식이 컨트롤 임을 지정 합니다.|
|[재구성](custom-cpp.md)|사용자 고유의 특성을 정의할 수 있습니다.|
|[db_column](db-column.md)|지정 된 열을 행 집합에 바인딩합니다.|
|[db_command](db-command.md)|OLE DB 명령을 만듭니다.|
|[db_param](db-param.md)|지정 된 멤버 변수를 입력 또는 출력 매개 변수와 연결 하 고 변수를 구분 합니다.|
|[db_source](db-source.md)|데이터 원본에 대 한 연결을 만듭니다.|
|[db_table](db-table.md)|OLE DB 테이블을 엽니다.|
|[default](default-cpp.md)|coclass 내에 정의된 custom 또는 dispinterface가 기본 프로그래밍 인터페이스를 나타낸다는 것을 의미합니다.|
|[defaultvtable](defaultvtable.md)|인터페이스를 컨트롤의 기본 vtable 인터페이스로 정의 합니다.|
|[event_receiver](event-receiver.md)|이벤트 수신기를 만듭니다.|
|[event_source](event-source.md)|이벤트 소스를 만듭니다.|
|[내보내기가](export.md)|데이터 구조가 .idl 파일에 배치 되도록 합니다.|
|[first_is](first-is.md)|전송할 첫 번째 배열 요소의 인덱스를 지정 합니다.|
|[은선제거](hidden.md)|항목이 존재 하지만 사용자 지향 브라우저에 표시 되지 않음을 나타냅니다.|
|[implements_category](implements-category.md)|클래스에 대해 구현 된 구성 요소 범주를 지정 합니다.|
|[last_is](last-is.md)|전송할 마지막 배열 요소의 인덱스를 지정 합니다.|
|[length_is](length-is.md)|전송할 배열 요소의 수를 지정 합니다.|
|[max_is](max-is.md)|유효한 배열 인덱스에 대 한 최대값을 지정 합니다.|
|[requires_category](requires-category.md)|대상 클래스의 필수 구성 요소 범주를 지정 합니다.|
|[size_is](size-is.md)|크기가 지정 된 포인터에 대해 할당 된 메모리 크기, 크기가 지정 된 포인터에 대 한 포인터 크기 조정 및 단일 또는 다차원 배열을 지정 합니다.|
|[source](source-cpp.md)|클래스에서 연결 지점의 COM 개체에 대 한 소스 인터페이스를 지정 합니다. 속성이 나 메서드에서는 멤버가 이벤트 소스인 개체 또는 변형을 반환 함을 나타냅니다.|
|[스레딩을](threading-cpp.md)|COM 개체의 스레딩 모델을 지정 합니다.|
|[unique](unique-cpp.md)|고유 포인터를 지정 합니다.|
|[uuid](uuid-cpp-attributes.md)|클래스 또는 인터페이스의 고유 ID를 지정 합니다.|
|[version](version-cpp.md)|클래스의 여러 버전에서 특정 버전을 식별 합니다.|
|[vi_progid](vi-progid.md)|ProgID의 버전 독립적 형식을 지정 합니다.|

## <a name="see-also"></a>참고 항목

[사용 별 특성](attributes-by-usage.md)
