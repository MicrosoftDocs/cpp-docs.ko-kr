---
description: '자세히 알아보기: 인터페이스 특성'
title: 인터페이스 특성 (c + + COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
ms.openlocfilehash: 4a2584f6d0ad73427c9460cd5ddafb92d11db9b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118331"
---
# <a name="interface-attributes"></a>인터페이스 특성

다음 특성은 [interface (또는 __interface)](../../cpp/interface.md) c + + 키워드에 적용 됩니다.

|특성|설명|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|COM 인터페이스의 동기 버전과 비동기 버전을 모두 정의 하도록 MIDL 컴파일러에 지시 하는 UUID를 지정 합니다.|
|[재구성](custom-cpp.md)|사용자 고유의 특성을 정의할 수 있습니다.|
|[dispinterface](dispinterface.md)|.Idl 파일의 인터페이스를 디스패치 인터페이스로 배치합니다.|
|[복수](dual.md)|인터페이스를 .idl 파일에 이중 인터페이스로 배치 합니다.|
|[내보내기가](export.md)|데이터 구조가 .idl 파일에 배치 되도록 합니다.|
|[helpcontext](helpcontext.md)|사용자가 도움말 파일에서이 요소에 대 한 정보를 볼 수 있는 컨텍스트 ID를 지정 합니다.|
|[helpfile](helpfile.md)|형식 라이브러리에 대 한 도움말 파일의 이름을 설정 합니다.|
|[helpstring](helpstring.md)|적용되는 요소를 설명하는 데 사용되는 문자열을 지정합니다.|
|[helpstringcontext](helpstringcontext.md)|.Hlp 또는 .chm 파일에 있는 도움말 항목의 ID를 지정 합니다.|
|[typelib](helpstringdll.md)|문서 문자열 조회 (지역화)를 수행 하는 데 사용할 DLL의 이름을 지정 합니다.|
|[은선제거](hidden.md)|항목이 존재 하지만 사용자 지향 브라우저에 표시 되지 않음을 나타냅니다.|
|[library_block](library-block.md)|.Idl 파일의 라이브러리 블록 안에 구문을 배치 합니다.|
|[로컬](local-cpp.md)|인터페이스 헤더에서 사용 하는 경우 MIDL 컴파일러를 헤더 생성기로 사용할 수 있습니다. 개별 함수에서 사용 하는 경우 스텁이 생성 되지 않는 지역 프로시저를 지정 합니다.|
|[nonextensible](nonextensible.md)|`IDispatch`구현 시 인터페이스 설명에 나열 된 속성 및 메서드만 포함 하 고 런타임에 추가 멤버로 확장할 수 없도록 지정 합니다. 이 특성은 [이중](dual.md) 인터페이스 에서만 유효 합니다.|
|[odl](odl.md)|인터페이스를 ODL (개체 설명 언어) 인터페이스로 식별 합니다.|
|[object](object-cpp.md)|사용자 지정 인터페이스를 식별 합니다.|
|[oleautomation](oleautomation.md)|인터페이스가 자동화와 호환 됨을 나타냅니다.|
|[pointer_default](pointer-default.md)|매개 변수 목록에 표시 되는 최상위 포인터를 제외 하 고 모든 포인터에 대 한 기본 포인터 특성을 지정 합니다.|
|[ptr](ptr.md)|포인터를 전체 포인터로 지정 합니다.|
|[액세스가](restricted.md)|임의로 호출할 수 없는 라이브러리의 멤버를 지정 합니다.|
|[uuid](uuid-cpp-attributes.md)|라이브러리의 고유 ID를 제공 합니다.|

인터페이스를 정의 하려면 다음 규칙을 따라야 합니다.

- 기본 호출 규칙은 [__stdcall](../../cpp/stdcall.md)입니다.

- GUID를 제공 하지 않으면 GUID가 제공 됩니다.

- 오버 로드 된 메서드는 허용 되지 않습니다.

다른 특성 프로젝트에서 [uuid](uuid-cpp-attributes.md) 특성을 지정 하지 않고 동일한 인터페이스 이름을 사용 하는 경우 동일한 GUID가 생성 됩니다.

## <a name="see-also"></a>참고 항목

[사용 별 특성](attributes-by-usage.md)
