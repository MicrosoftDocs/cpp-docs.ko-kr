---
description: '다음에 대 한 자세한 정보: IDL 특성'
title: IDL 특성 (c + + COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- IDL attributes
- .idl files [C++], attributes
- IDL files [C++], attributes
- .idl files [C++]
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
ms.openlocfilehash: 1db49b6c68d0dd4e4f4c6c5dcfb148cafc39159d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275466"
---
# <a name="idl-attributes"></a>IDL 특성

일반적으로 .idl 파일을 유지 관리 하는 경우 다음을 수행 해야 했습니다.

- 수정할 수 있는 .idl 파일의 구조 및 구문에 대해 잘 알고 있어야 합니다.

- .Idl 파일의 일부 측면을 수정할 수 있는 마법사를 사용 합니다.

이제 Visual C++ IDL 특성을 사용 하 여 소스 코드 파일 내에서 .idl 파일을 수정할 수 있습니다. 대부분의 경우 Visual C++ IDL 특성의 이름은 MIDL 특성과 동일 합니다. Visual C++ IDL 특성과 MIDL 특성의 이름이 같으면 소스 코드 파일에 Visual C++ 특성을 넣으면 마다 MIDL 특성을 포함 하는 .idl 파일이 생성 됩니다. 그러나 Visual C++ IDL 특성은 MIDL 특성의 일부 기능을 제공 하지 않을 수 있습니다.

[COM 특성과](com-attributes.md)함께 사용 되지 않는 경우에는 IDL 특성에서 인터페이스를 정의할 수 있습니다. 소스 코드가 컴파일되면 생성 된 .idl 파일을 정의 하는 데 특성이 사용 됩니다. ATL 프로젝트에서 COM 특성과 함께 사용 되는 경우와 같은 일부 IDL 특성은 `coclass` 코드를 프로젝트에 삽입 합니다.

[Idl_quote](idl-quote.md) 에서는 현재 버전의 Visual C++에서 지원 되지 않는 MIDL 구문을 사용할 수 있습니다. 이 특성과 [importlib](importlib.md) 및 [includelib](includelib-cpp.md) 와 같은 기타 특성을 사용 하면 현재 Visual Studio c + + 프로젝트에서 기존 .idl 파일을 사용 하는 데 도움이 됩니다.

|특성|설명|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|다른 컨트롤에서 컨트롤을 집계할 수 있음을 나타냅니다.|
|[appobject](appobject.md)|Coclass를 전체 EXE 응용 프로그램과 연결 된 응용 프로그램 개체로 식별 하 고 coclass의 함수 및 속성을이 형식 라이브러리에서 전역적으로 사용할 수 있음을 나타냅니다.|
|[async_uuid](async-uuid.md)|COM 인터페이스의 동기 버전과 비동기 버전을 모두 정의 하도록 MIDL 컴파일러에 지시 하는 UUID를 지정 합니다.|
|[bindable](bindable.md)|속성이 데이터 바인딩을 지원합니다.|
|[call_as](call-as.md)|원격화 할 수 없는 함수를 원격 함수에 매핑할 수 있도록 합니다.|
|[case](case-cpp.md)|Union의 [switch_type](switch-type.md) 특성과 함께 사용 됩니다.|
|[coclass](coclass.md)|클래스 정의를 .idl 파일에 coclass로 배치 합니다.|
|[control](control.md)|사용자 정의 형식이 컨트롤 임을 지정 합니다.|
|[cpp_quote](cpp-quote.md)|지정 된 문자열을 인용 문자 없이 생성 된 헤더 파일에 내보냅니다.|
|[defaultbind](defaultbind.md)|개체를 가장 잘 나타내는 바인딩 가능한 단일 속성을 나타냅니다.|
|[defaultcollelem](defaultcollelem.md)|Visual Basic 코드 최적화에 사용 됩니다.|
|[defaultvalue](defaultvalue.md)|형식화 된 선택적 매개 변수에 기본값을 지정할 수 있습니다.|
|[default](default-cpp.md)|coclass 내에 정의된 custom 또는 dispinterface가 기본 프로그래밍 인터페이스를 나타낸다는 것을 의미합니다.|
|[defaultvtable](defaultvtable.md)|인터페이스를 컨트롤의 기본 vtable 인터페이스로 정의 합니다.|
|[dispinterface](dispinterface.md)|.Idl 파일의 인터페이스를 디스패치 인터페이스로 배치합니다.|
|[displaybind](displaybind.md)|사용자에 게 바인딩 가능으로 표시 해야 하는 속성을 나타냅니다.|
|[복수](dual.md)|인터페이스를 .idl 파일에 이중 인터페이스로 배치 합니다.|
|[엔트리의](entry.md)|DLL의 진입점을 식별 하 여 모듈에서 내보낸 함수 또는 상수를 지정 합니다.|
|[first_is](first-is.md)|전송할 첫 번째 배열 요소의 인덱스를 지정 합니다.|
|[helpcontext](helpcontext.md)|사용자가 도움말 파일에서이 요소에 대 한 정보를 볼 수 있는 컨텍스트 ID를 지정 합니다.|
|[helpfile](helpfile.md)|형식 라이브러리에 대 한 도움말 파일의 이름을 설정 합니다.|
|[helpstringcontext](helpstringcontext.md)|.Hlp 또는 .chm 파일에 있는 도움말 항목의 ID를 지정 합니다.|
|[typelib](helpstringdll.md)|문서 문자열 조회 (지역화)를 수행 하는 데 사용할 DLL의 이름을 지정 합니다.|
|[helpstring](helpstring.md)|적용되는 요소를 설명하는 데 사용되는 문자열을 지정합니다.|
|[은선제거](hidden.md)|항목이 존재 하지만 사용자 지향 브라우저에 표시 되지 않음을 나타냅니다.|
|[idl_module](idl-module.md)|DLL의 진입점을 지정 합니다.|
|[idl_quote](idl-quote.md)|Visual C++ 현재 버전에서 지원 되지 않는 특성 또는 IDL 구문을 사용할 수 있습니다.|
|[id](id.md)|인터페이스 또는 인터페이스에서 멤버 함수 (속성 또는 메서드)에 대 한 DISPID를 지정 합니다.|
|[iid_is](iid-is.md)|인터페이스 포인터가 가리키는 COM 인터페이스의 IID를 지정 합니다.|
|[immediatebind](immediatebind.md)|데이터 바인딩된 개체의 속성에 대 한 모든 변경 내용이 데이터베이스에 즉시 전달 됨을 나타냅니다.|
|[importlib](importlib.md)|다른 형식 라이브러리에 이미 컴파일된 형식을 만들고 있는 형식 라이브러리에서 사용할 수 있도록 합니다.|
|[import](import.md)|기본 .idl 파일에서 참조 하려는 정의가 포함 된 다른 .idl, odl 또는 헤더 파일을 지정 합니다.|
|[되어야](include-cpp.md)|생성 된 .idl 파일에 포함할 하나 이상의 헤더 파일을 지정 합니다.|
|[includelib](includelib-cpp.md)|.Idl 또는 .h 파일을 생성 된 .idl 파일에 포함 시킵니다.|
|[in](in-cpp.md)|호출 하는 프로시저에서 호출 되는 프로시저로 매개 변수가 전달 됨을 나타냅니다.|
|[last_is](last-is.md)|전송할 마지막 배열 요소의 인덱스를 지정 합니다.|
|[lcid](lcid.md)|로캘 식별자를 함수에 전달할 수 있습니다.|
|[length_is](length-is.md)|전송할 배열 요소의 수를 지정 합니다.|
|[사용권이](licensed.md)|는 적용 되는 coclass가 사용이 허가 되 고를 사용 하 여 인스턴스화해야 함을 나타냅니다 `IClassFactory2` .|
|[로컬](local-cpp.md)|인터페이스 헤더에서 사용 하는 경우 MIDL 컴파일러를 헤더 생성기로 사용할 수 있습니다. 개별 함수에서 사용 하는 경우 스텁이 생성 되지 않는 지역 프로시저를 지정 합니다.|
|[max_is](max-is.md)|유효한 배열 인덱스에 대 한 최대값을 지정 합니다.|
|[모듈](module-cpp.md)|.Idl 파일의 라이브러리 블록을 정의합니다.|
|[ms_union](ms-union.md)|캡슐화 되지 않은 공용 구조체의 네트워크 데이터 표현 맞춤을 제어 합니다.|
|[no_injected_text](no-injected-text.md)|컴파일러가 특성 사용의 결과로 코드를 삽입 하지 않도록 합니다.|
|[nonbrowsable](nonbrowsable.md)|인터페이스 멤버를 속성 브라우저에 표시 하지 않아야 함을 나타냅니다.|
|[noncreatable](noncreatable.md)|자체로 인스턴스화할 수 없는 개체를 정의 합니다.|
|[nonextensible](nonextensible.md)|`IDispatch`구현 시 인터페이스 설명에 나열 된 속성 및 메서드만 포함 하 고 런타임에 추가 멤버로 확장할 수 없도록 지정 합니다.|
|[object](object-cpp.md)|사용자 지정 인터페이스를 식별 합니다. 사용자 지정 특성과 동의어입니다.|
|[odl](odl.md)|인터페이스를 ODL (개체 설명 언어) 인터페이스로 식별 합니다.|
|[oleautomation](oleautomation.md)|인터페이스가 자동화와 호환 됨을 나타냅니다.|
|[필드](optional-cpp.md)|멤버 함수에 대 한 선택적 매개 변수를 지정 합니다.|
|[out](out-cpp.md)|호출된 프로시저에서 호출하는 프로시저로 반환된(서버에서 클라이언트로 반환된) 포인터 매개 변수를 식별합니다.|
|[pointer_default](pointer-default.md)|매개 변수 목록에 표시 되는 최상위 포인터를 제외 하 고 모든 포인터에 대 한 기본 포인터 특성을 지정 합니다.|
|[pragma](pragma.md)|지정 된 문자열을 인용 문자 없이 생성 된 .idl 파일로 내보냅니다.|
|[progid](progid.md)|COM 개체의 ProgID를 지정 합니다.|
|[propget](propget.md)|속성 접근자 (get) 함수를 지정 합니다.|
|[propputref](propputref.md)|값 대신 참조를 사용 하는 속성 설정 함수를 지정 합니다.|
|[propput](propput.md)|속성 설정 함수를 지정합니다.|
|[ptr](ptr.md)|포인터를 전체 포인터로 지정 합니다.|
|[public](public-cpp-attributes.md)|Idl 파일에서 참조 되지 않는 경우에도 형식 라이브러리에 typedef를 넣습니다.|
|[range](range-cpp.md)|런타임에 값이 설정 되는 인수 또는 필드에 허용 되는 값 범위를 지정 합니다.|
|[readonly](readonly-cpp.md)|변수에 대 한 할당을 금지 합니다.|
|[ref](ref-cpp.md)|참조 포인터를 식별 합니다.|
|[requestedit](requestedit.md)|속성이 `OnRequestEdit` 알림을 지원함을 나타냅니다.|
|[액세스가](restricted.md)|라이브러리, 모듈, 인터페이스 또는 인터페이스의 멤버를 임의로 호출할 수 없도록 지정 합니다.|
|[retval](retval.md)|멤버의 반환 값을 받는 매개 변수를 지정 합니다.|
|[size_is](size-is.md)|크기가 지정 된 포인터에 대해 할당 된 메모리 크기, 크기가 지정 된 포인터에 대 한 포인터 크기 조정 및 단일 또는 다차원 배열을 지정 합니다.|
|[source](source-cpp.md)|클래스, 속성 또는 메서드의 멤버가 이벤트의 소스 임을 나타냅니다.|
|[string](string-cpp.md)|1 차원 **`char`** , **`wchar_t`** , `byte` 또는 이와 동등한 배열이 나 해당 배열에 대 한 포인터를 문자열로 처리 해야 함을 나타냅니다.|
|[switch_is](switch-is.md)|Union 멤버를 선택 하는 union 판별 역할을 하는 식 또는 식별자를 지정 합니다.|
|[switch_type](switch-type.md)|Union 판별으로 사용 되는 변수의 형식을 식별 합니다.|
|[transmit_as](transmit-as.md)|클라이언트 및 서버 응용 프로그램에서 조작 된 형식을 전송 된 형식으로 연결 하도록 컴파일러에 지시 합니다.|
|[uidefault](uidefault.md)|형식 정보 멤버가 사용자 인터페이스에 표시 하기 위한 기본 멤버 임을 나타냅니다.|
|[unique](unique-cpp.md)|고유 포인터를 지정 합니다.|
|[usesgetlasterror](usesgetlasterror.md)|호출자가 해당 함수를 호출할 때 오류가 발생 하면 호출자가를 호출 하 여 오류 코드를 검색할 수 있음을 호출자에 `GetLastError` 게 알립니다.|
|[uuid](uuid-cpp-attributes.md)|클래스 또는 인터페이스의 고유 ID를 지정 합니다.|
|[v1_enum](v1-enum.md)|지정 된 열거형 형식이 16 비트 기본값이 아닌 32 비트 엔터티로 전송 되도록 지정 합니다.|
|[vararg](vararg.md)|함수에서 다양 한 수의 인수를 사용 하도록 지정 합니다.|
|[vi_progid](vi-progid.md)|ProgID의 버전 독립적 형식을 지정 합니다.|
|[wire_marshal](wire-marshal.md)|응용 프로그램별 데이터 형식 대신 전송에 사용 되는 데이터 형식을 지정 합니다.|

## <a name="see-also"></a>참고 항목

[그룹별 특성](attributes-by-group.md)
