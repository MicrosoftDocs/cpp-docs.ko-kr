---
description: '방법에 대 한 자세한 정보: 메서드 특성'
title: 메서드 특성 (c + + COM)
ms.date: 10/02/2018
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
ms.openlocfilehash: 29acb1f92b01e85960bc727c9b3e91f9a52732d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327499"
---
# <a name="method-attributes"></a>메서드 특성

다음 특성은 클래스, coclass 또는 인터페이스의 메서드에 적용 됩니다.

|특성|설명|
|---------------|-----------------|
|[bindable](bindable.md)|속성이 데이터 바인딩을 지원합니다.|
|[call_as](call-as.md)|원격화 할 수 없는 함수를 원격 함수에 매핑할 수 있도록 합니다.|
|[재구성](custom-cpp.md)|사용자 고유의 특성을 정의할 수 있습니다.|
|[db_column](db-column.md)|지정 된 열을 행 집합에 바인딩합니다.|
|[db_command](db-command.md)|OLE DB 명령을 만듭니다.|
|[db_param](db-param.md)|지정 된 멤버 변수를 입력 또는 출력 매개 변수와 연결 하 고 변수를 구분 합니다.|
|[db_source](db-source.md)|데이터 원본에 대 한 연결을 만듭니다.|
|[db_table](db-table.md)|OLE DB 테이블을 엽니다.|
|[defaultbind](defaultbind.md)|개체를 가장 잘 나타내는 바인딩 가능한 단일 속성을 나타냅니다.|
|[defaultcollelem](defaultcollelem.md)|Visual Basic 코드 최적화에 사용 됩니다.|
|[displaybind](displaybind.md)|사용자에 게 바인딩 가능으로 표시 해야 하는 속성을 나타냅니다.|
|[helpcontext](helpcontext.md)|사용자가 **도움말** 파일에서이 요소에 대 한 정보를 볼 수 있는 컨텍스트 ID를 지정 합니다.|
|[helpfile](helpfile.md)|형식 라이브러리에 대 한 **도움말** 파일의 이름을 설정 합니다.|
|[helpstring](helpstring.md)|적용되는 요소를 설명하는 데 사용되는 문자열을 지정합니다.|
|[helpstringcontext](helpstringcontext.md)|.Hlp 또는 .chm 파일에 있는 도움말 항목의 ID를 지정 합니다.|
|[typelib](helpstringdll.md)|문서 문자열 조회 (지역화)를 수행 하는 데 사용할 DLL의 이름을 지정 합니다.|
|[은선제거](hidden.md)|항목이 존재 하지만 사용자 지향 브라우저에 표시 되지 않음을 나타냅니다.|
|[id](id.md)|인터페이스 또는 인터페이스에서 멤버 함수 (속성 또는 메서드)에 대 한 DISPID를 지정 합니다.|
|[immediatebind](immediatebind.md)|데이터 바인딩된 개체의 속성에 대 한 모든 변경 내용이 데이터베이스에 즉시 전달 됨을 나타냅니다.|
|[in](in-cpp.md)|호출 하는 프로시저에서 호출 되는 프로시저로 매개 변수가 전달 됨을 나타냅니다.|
|[로컬](local-cpp.md)|인터페이스 헤더에서 사용 하는 경우 MIDL 컴파일러를 헤더 생성기로 사용할 수 있습니다. 개별 함수에서 사용 하는 경우 스텁이 생성 되지 않는 지역 프로시저를 지정 합니다.|
|[nonbrowsable](nonbrowsable.md)|인터페이스 멤버를 속성 브라우저에 표시 하지 않아야 함을 나타냅니다.|
|[propget](propget.md)|속성 접근자 함수를 지정 합니다.|
|[propput](propput.md)|속성 설정 함수를 지정 합니다.|
|[propputref](propputref.md)|값 대신 참조를 사용 하는 속성 설정 함수를 지정 합니다.|
|[ptr](ptr.md)|포인터를 전체 포인터로 지정 합니다.|
|[range](range-cpp.md)|런타임에 값이 설정 되는 인수 또는 필드에 허용 되는 값 범위를 지정 합니다.|
|[requestedit](requestedit.md)|속성이 `OnRequestEdit` 알림을 지원함을 나타냅니다.|
|[액세스가](restricted.md)|모듈, 인터페이스 또는 인터페이스의 멤버를 임의로 호출할 수 없도록 지정 합니다.|
|[satype](satype.md)|구조체의 데이터 형식을 지정 합니다 `SAFEARRAY` .|
|[source](source-cpp.md)|클래스의 연결 점에 대 한 컨트롤의 소스 인터페이스를 지정 합니다. 속성이 나 메서드에서 `source` 특성은 멤버가 이벤트 소스인 개체 또는 변형을 반환 함을 나타냅니다.|
|[항목과](synchronize.md)|대상 메서드에 대 한 액세스를 동기화 합니다.|
|[vararg](vararg.md)|함수에서 다양 한 수의 인수를 사용 하도록 지정 합니다.|

## <a name="see-also"></a>참고 항목

[사용 별 특성](attributes-by-usage.md)
