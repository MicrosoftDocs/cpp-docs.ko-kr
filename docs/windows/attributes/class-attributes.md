---
description: '자세히 알아보기: 클래스 특성'
title: 클래스 특성 (c + + COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
ms.openlocfilehash: ea929ed7f5fac949393e6d3cf2b24195babfeea7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247386"
---
# <a name="class-attributes"></a>클래스 특성

다음 특성은 [클래스](../../cpp/class-cpp.md) c + + 키워드에 적용 됩니다.

|특성|설명|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|클래스가 집계를 지원함을 나타냅니다.|
|[집계](aggregates.md)|컨트롤이 대상 클래스를 집계 함을 나타냅니다.|
|[appobject](appobject.md)|Coclass를 전체 .exe 응용 프로그램과 연결 된 응용 프로그램 개체로 식별 하 고 coclass의 함수 및 속성을이 형식 라이브러리에서 전역적으로 사용할 수 있음을 나타냅니다.|
|[case](case-cpp.md)|Union의 [switch_type](switch-type.md) 특성과 함께 사용 됩니다.|
|[coclass](coclass.md)|ActiveX 컨트롤을 만듭니다.|
|[com_interface_entry](com-interface-entry-cpp.md)|인터페이스 항목을 COM 맵에 추가 합니다.|
|[control](control.md)|사용자 정의 형식이 컨트롤 임을 지정 합니다.|
|[재구성](custom-cpp.md)|사용자 고유의 특성을 정의할 수 있습니다.|
|[db_command](db-command.md)|OLE DB 명령을 만듭니다.|
|[db_param](db-param.md)|지정 된 멤버 변수를 입력 또는 출력 매개 변수와 연결 하 고 변수를 구분 합니다.|
|[db_source](db-source.md)|데이터 원본에 대 한 연결을 만듭니다.|
|[db_table](db-table.md)|OLE DB 테이블을 엽니다.|
|[default](default-cpp.md)|coclass 내에 정의된 custom 또는 dispinterface가 기본 프로그래밍 인터페이스를 나타낸다는 것을 의미합니다.|
|[defaultvtable](defaultvtable.md)|인터페이스를 컨트롤의 기본 vtable 인터페이스로 정의 합니다.|
|[event_receiver](event-receiver.md)|이벤트 수신기를 만듭니다.|
|[event_source](event-source.md)|이벤트 소스를 만듭니다.|
|[helpcontext](helpcontext.md)|사용자가 **도움말** 파일에서이 요소에 대 한 정보를 볼 수 있는 컨텍스트 ID를 지정 합니다.|
|[helpfile](helpfile.md)|형식 라이브러리에 대 한 도움말 파일의 이름을 설정 합니다.|
|[helpstringcontext](helpstringcontext.md)|.Hlp 또는 .chm 파일에 있는 도움말 항목의 ID를 지정 합니다.|
|[helpstring](helpstring.md)|적용되는 요소를 설명하는 데 사용되는 문자열을 지정합니다.|
|[은선제거](hidden.md)|항목이 존재 하지만 사용자 지향 브라우저에 표시 되지 않음을 나타냅니다.|
|[구현할](implements-cpp.md)|IDL coclass의 멤버가 되도록 강제 적용 되는 디스패치 인터페이스를 지정 합니다.|
|[implements_category](implements-category.md)|클래스에 대해 구현 된 구성 요소 범주를 지정 합니다.|
|[모듈](module-cpp.md)|.Idl 파일의 라이브러리 블록을 정의합니다.|
|[noncreatable](noncreatable.md)|자체로 인스턴스화할 수 없는 개체를 정의 합니다.|
|[progid](progid.md)|컨트롤의 ProgID를 정의 합니다.|
|[registration_script](registration-script.md)|지정 된 등록 스크립트를 실행 합니다.|
|[requestedit](requestedit.md)|속성이 `OnRequestEdit` 알림을 지원함을 나타냅니다.|
|[source](source-cpp.md)|클래스의 연결 점에 대 한 컨트롤의 소스 인터페이스를 지정 합니다. 속성이 나 메서드에서 `source` 특성은 멤버가 개체를 반환 하거나 이벤트 소스인 것을 나타냅니다 `VARIANT` .|
|[support_error_info](support-error-info.md)|대상 개체에 대 한 오류 보고를 지원 합니다.|
|[스레딩을](threading-cpp.md)|컨트롤의 스레딩 모델을 지정 합니다.|
|[uuid](uuid-cpp-attributes.md)|클래스 또는 인터페이스의 고유 ID를 지정 합니다.|
|[version](version-cpp.md)|클래스의 여러 버전에서 특정 버전을 식별 합니다.|
|[vi_progid](vi-progid.md)|ProgID의 버전 독립적 형식을 지정 합니다.|

## <a name="see-also"></a>참고 항목

[사용 별 특성](attributes-by-usage.md)
